import React, { useState, useEffect } from 'react'
import { TouchableOpacity } from 'react-native';
import {
  Box,
  View as ViewBase,
  Text,
  NativeBaseProvider,
  Input,
  Icon,
  HStack
} from 'native-base';
import Feather from 'react-native-vector-icons/Feather'

export default function App() {

  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');

  const [objUser, setObjUser] = useState({
    username: '',
    password: '',
  });

  const onClickLoginHandler = () => {
    console.log(objUser);
  }

  return (
    <NativeBaseProvider>
      <Box safeAreaTop bg={'gray.200'} />
      <Box flex={1} bg={'gray.200'}>
        <Box flex={1} justifyContent={'center'} alignItems={'center'} >
          <Text fontSize={'2xl'} fontWeight={'bold'} m={2} >{'Login'}</Text>
          <Box bg={'white'} w={'90%'} p={2} borderRadius={10} >
            <Input
              value={objUser.username}
              onChangeText={(text) => setObjUser({ ...objUser, username: text })}
              m={1}
              p={2}
              borderRadius={5}
              fontSize={'lg'}
              placeholder={'Username'}
              InputLeftElement={<Icon as={<Feather name="user" />} size={5} ml="2" color="muted.400" />}
            />
            <Input
              value={objUser.password}
              onChangeText={(text) => setObjUser({ ...objUser, password: text })}
              m={1}
              p={2}
              borderRadius={5}
              fontSize={'lg'}
              placeholder={'Password'}
              InputRightElement={<Icon as={<Feather name="key" />} size={5} mr="2" color="muted.400" />}
            />
            <Box m={1} />
            <TouchableOpacity
              style={{ backgroundColor: 'blue', alignItems: 'center', height: 34, justifyContent: 'center', borderRadius: 10 }}
              onPress={() => { onClickLoginHandler() }}
            >
              <HStack alignItems={'center'} justifyContent={'space-between'} w={'100%'} p={2} >
                <Text fontWeight={'bold'} color={'white'}>{'Login'}</Text>
                <Icon as={<Feather name='arrow-right-circle' />} size={'md'} color={'white'} />
              </HStack>
            </TouchableOpacity>
            <Box m={1} />
            <TouchableOpacity
              style={{ backgroundColor: 'red', alignItems: 'center', height: 34, justifyContent: 'center', borderRadius: 10 }}
              onPress={() => {
                setObjUser({
                  username: '',
                  password: '',
                })
              }}
            >
              <HStack alignItems={'center'} justifyContent={'space-between'} w={'100%'} p={2} >
                <Text fontWeight={'bold'} color={'white'}>{'Cancel'}</Text>
                <Icon as={<Feather name='x-circle' />} size={'md'} color={'white'} />
              </HStack>


            </TouchableOpacity>
          </Box>
        </Box>
      </Box>
      <Box safeAreaBottom bg={'gray.200'} />
    </NativeBaseProvider>
  )
}

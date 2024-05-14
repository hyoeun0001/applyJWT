# JWT 적용 및 users의 login 로직
쿠키 설정 및 JWT 유효기간 설정
- 개념 : JSON 형태의 데이터를 안전하게 전송하기 위한 웹에서 사용하는 토큰
- 구조
  - 헤더 : 토큰을 암호화 하는데 사용하는 알고리즘, 토큰의 형태(jwt)
  - 페이로드 : 사용자 정보(이름, 주소, 핸드폰, …비밀번호X)
  - 서명 : 만약 페이로드 값이 바뀌면 서명 값이 통으로 바뀐다. 때문에 우리는 JWT를 믿고 쓸 수 있다.
```
//token발급
                        const token = jwt.sign({
                            email : loginUser.email,
                            name : loginUser.name
                        }, process.env.PRIVATE_KEY, {
                            expiresIn : '5m',
                            issuer : "songa"
                        });

                        res.cookie("token",token,{
                            httpOnly : true
                        })
```

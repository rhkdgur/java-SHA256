# java-SHA256
SHA256 단방향 암호화 코드

```C
  public class SHA256 {
	
	public String getSHA256(String key) {
		StringBuffer result = new StringBuffer();
		
		try {
			MessageDigest digest = MessageDigest.getInstance("SHA-256");
			byte[] salt = "123456789".getBytes(StandardCharsets.UTF_8);
			digest.reset();
			digest.update(salt);
			byte[] chars = digest.digest(key.getBytes("UTF-8"));
			for(int i = 0; i<chars.length; i++)
			{
				String hex = Integer.toHexString(0xff & chars[i]);
				if(hex.length() < 2)
					result.append("0");
				
				result.append(hex);
			}
		}catch(Exception e) {
			e.printStackTrace();
			result = null;
		}
		
		
		return result.toString();
	}

}

```

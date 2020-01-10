---
title: 'Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
ms.openlocfilehash: 8ca4c4c5b1257411ecdf86858040bf428a9e6ce0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706064"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama
Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır. Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir. Anahtar kapsayıcıları hakkında daha fazla bilgi için bkz. [makine düzeyi ve Kullanıcı DÜZEYI RSA anahtar kapsayıcılarını anlama](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Asimetrik anahtar oluşturmak ve anahtarı bir anahtar kapsayıcısına kaydetmek için  
  
1. <xref:System.Security.Cryptography.CspParameters> sınıfının yeni bir örneğini oluşturun ve anahtar kapsayıcısını çağırmak istediğiniz adı <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> alanına geçirin.  
  
2. <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfından (genellikle **RSACryptoServiceProvider** veya **DSACryptoServiceProvider**) türetilen bir sınıfın yeni bir örneğini oluşturun ve önceden oluşturulan **CspParameters** nesnesini oluşturucuya geçirin.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Anahtar kapsayıcısından anahtarı silmek için  
  
1. **CspParameters** sınıfının yeni bir örneğini oluşturun ve anahtar kapsayıcısını, **CspParameters. KeyContainerName** alanına çağırmak istediğiniz adı geçirin.  
  
2. **AsymmetricAlgorithm** sınıfından (genellikle **RSACryptoServiceProvider** veya **DSACryptoServiceProvider**) türetilen bir sınıfın yeni bir örneğini oluşturun ve önceden oluşturulan **CspParameters** nesnesini oluşturucuya geçirin.  
  
3. **AsymmetricAlgorithm** sınıfından türetilen sınıfın **Persistkeyincsp** özelliğini **false** olarak ayarlayın (Visual Basic için**false** ).  
  
4. **AsymmetricAlgorithm**türetilen sınıfın **clear** metodunu çağırın. Bu yöntem, sınıfın tüm kaynaklarını serbest bırakır ve anahtar kapsayıcısını temizler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, asimetrik anahtar oluşturmayı, anahtar kapsayıcısına kaydetmeyi, daha sonra anahtarı almayı ve kapsayıcıyı kapsayıcıdan silmeyi gösterir.  
  
 `GenKey_SaveInContainer` yöntemi ve `GetKeyFromContainer` yöntemi içindeki kodun benzer olduğuna dikkat edin.  <xref:System.Security.Cryptography.CspParameters> nesnesi için bir anahtar kapsayıcı adı belirttiğinizde ve bunu <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği veya <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği true olarak ayarlanan bir <xref:System.Security.Cryptography.AsymmetricAlgorithm> nesnesine geçirdiğinizde, aşağıdakiler gerçekleşir.  Belirtilen ada sahip bir anahtar kapsayıcısı yoksa, bir tane oluşturulur ve anahtar kalıcıdır.  Belirtilen ada sahip bir anahtar kapsayıcısı varsa, kapsayıcıdaki anahtar geçerli <xref:System.Security.Cryptography.AsymmetricAlgorithm> nesnesine otomatik olarak yüklenir.  Bu nedenle, `GenKey_SaveInContainer` yöntemindeki kod, ilk kez çalıştırıldığı için anahtarı devam ettirir, ancak `GetKeyFromContainer` yöntemindeki kod ikinci çalıştırıldığı için anahtarı yükler.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```console  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Veri Şifreleme](../../../docs/standard/security/encrypting-data.md)
- [Verilerin Şifresini Çözme](../../../docs/standard/security/decrypting-data.md)
- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

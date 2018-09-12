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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5cd157f89797406fbe87c3d70c415d7b192d1a9
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508516"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama
Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır. Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir. Anahtar kapsayıcıları hakkında daha fazla bilgi için bkz. [anlama makine düzeyinde ve kullanıcı düzeyi RSA anahtar kapsayıcılarının](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Asimetrik bir anahtar oluşturun ve bir anahtar kapsayıcısında kaydetmek için  
  
1.  Yeni bir örneğini oluşturmak bir <xref:System.Security.Cryptography.CspParameters> sınıfı ve anahtar kapsayıcısına aramak istediğiniz adı geçirin <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> alan.  
  
2.  Türetilen bir sınıfın yeni bir örneğini oluşturma <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfı (genellikle **RSACryptoServiceProvider** veya **DSACryptoServiceProvider**) ve önceden oluşturulmuş  **CspParameters** nesnesine, yapıcısına.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Anahtarı bir anahtar kapsayıcısından silinemedi  
  
1.  Yeni bir örneğini oluşturmak bir **CspParameters** sınıfı ve anahtar kapsayıcısına aramak istediğiniz adı geçirin **CspParameters.KeyContainerName** alan.  
  
2.  Türetilen bir sınıfın yeni bir örneğini oluşturma **AsymmetricAlgorithm** sınıfı (genellikle **RSACryptoServiceProvider** veya **DSACryptoServiceProvider**) ve geçirin daha önce oluşturduğunuz **CspParameters** nesnesine, yapıcısına.  
  
3.  Ayarlama **PersistKeyInCSP** , türetilen sınıfın özelliği **AsymmetricAlgorithm** için **false** (**False** Visual Basic'te).  
  
4.  Çağrı **Temizle** yöntem, türetilen sınıfın **AsymmetricAlgorithm**. Bu yöntem, sınıfın tüm kaynakları serbest bırakır ve anahtar kapsayıcısı temizler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, asimetrik anahtar oluşturma, bir anahtar kapsayıcısında kaydedin, daha sonra anahtarı alamazsınız ve anahtar kapsayıcısından silin gösterilmektedir.  
  
 Kodda fark `GenKey_SaveInContainer` yöntemi ve `GetKeyFromContainer` yöntemi benzerdir.  İçin bir anahtar kapsayıcısı adını belirtirseniz bir <xref:System.Security.Cryptography.CspParameters> geçirin ve nesne bir <xref:System.Security.Cryptography.AsymmetricAlgorithm> nesnesi ile <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği veya <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği true, aşağıdakiler gerçekleşir ayarlayın.  Belirtilen ada sahip bir anahtar kapsayıcı mevcut değilse, ardından bir oluşturulur ve anahtar kalıcı hale getirilir.  Belirtilen ada sahip bir anahtar kapsayıcısı mevcut sonra anahtar kapsayıcısında geçerli otomatik olarak yüklenen <xref:System.Security.Cryptography.AsymmetricAlgorithm> nesne.  Bu nedenle, kodda `GenKey_SaveInContainer` yöntemi kodunda çalışırken ilk çalıştığından anahtar devam ederse `GetKeyFromContainer` yöntemi ikinci çalıştığından anahtarı yükler.  
  
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
  
```Output  
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

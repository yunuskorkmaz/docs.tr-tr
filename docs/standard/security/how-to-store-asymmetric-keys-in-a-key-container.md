---
title: 'Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 20
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eece5dbcab1e81d9f9a2a5dd9e6ed42da108b09c
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama
Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır. Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir. Anahtar kapsayıcıları hakkında daha fazla bilgi için bkz: [anlama makine düzeyinde ve kullanıcı düzeyinde RSA anahtar kapsayıcıları](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Asimetrik anahtar oluşturmak ve bir anahtar kapsayıcısında kaydetmek için  
  
1.  Yeni bir örneğini oluşturmak bir <xref:System.Security.Cryptography.CspParameters> sınıfı ve anahtar kapsayıcısı aramak istediğiniz adı <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> alan.  
  
2.  Türetilen sınıfın yeni bir örnek oluşturmak <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfı (genellikle **RSACryptoServiceProvider** veya **DSACryptoServiceProvider**) ve daha önce oluşturulmuş geçirin  **CspParameters** kendi oluşturucuya nesnesi.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Bir anahtar kapsayıcı anahtarını silmek için  
  
1.  Yeni bir örneğini oluşturmak bir **CspParameters** sınıfı ve anahtar kapsayıcısı aramak istediğiniz adı **CspParameters.KeyContainerName** alan.  
  
2.  Türetilen sınıfın yeni bir örnek oluşturmak **AsymmetricAlgorithm** sınıfı (genellikle **RSACryptoServiceProvider** veya **DSACryptoServiceProvider**) ve geçirin daha önce oluşturduğunuz **CspParameters** kendi oluşturucuya nesnesi.  
  
3.  Ayarlama **PersistKeyInCSP** türetildiği sınıfın özelliği **AsymmetricAlgorithm** için **false** (**False** Visual Basic'te).  
  
4.  Çağrı **Temizle** yöntemi türetildiği sınıfın **AsymmetricAlgorithm**. Bu yöntem sınıfın tüm kaynakları serbest bırakır ve anahtar kapsayıcısı temizler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir asimetrik anahtar oluşturmak, bir anahtar kapsayıcısında kaydedin, daha sonraki bir zamanda anahtarı almak ve anahtarı kapsayıcısından silin gösterilmiştir.  
  
 Bu kodu fark `GenKey_SaveInContainer` yöntemi ve `GetKeyFromContainer` yöntemi benzer.  İçin bir anahtar kapsayıcı adı belirttiğinizde bir <xref:System.Security.Cryptography.CspParameters> nesne ve ona geçirin bir <xref:System.Security.Cryptography.AsymmetricAlgorithm> nesnesi ile <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği veya <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği true, şunlar olur ayarlayın.  Belirtilen ada sahip bir anahtar kapsayıcısı mevcut değilse, ardından oluşturulur ve anahtar kalıcı.  Belirtilen ada sahip bir anahtar kapsayıcısı yok sonra anahtar kapsayıcısında geçerli otomatik olarak yüklenen <xref:System.Security.Cryptography.AsymmetricAlgorithm> nesnesi.  Bu nedenle, kodda `GenKey_SaveInContainer` yöntemi devam ederse anahtar kodda sırasında ilk çalıştığından `GetKeyFromContainer` yöntemi ikinci çalıştığından anahtarı yükler.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [Veri Şifreleme](../../../docs/standard/security/encrypting-data.md)  
 [Verilerin Şifresini Çözme](../../../docs/standard/security/decrypting-data.md)  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

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
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="9c71e-102">Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama</span><span class="sxs-lookup"><span data-stu-id="9c71e-102">How to: Store Asymmetric Keys in a Key Container</span></span>
<span data-ttu-id="9c71e-103">Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c71e-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="9c71e-104">Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c71e-104">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="9c71e-105">Anahtar kapsayıcıları hakkında daha fazla bilgi için bkz: [anlama makine düzeyinde ve kullanıcı düzeyinde RSA anahtar kapsayıcıları](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).</span><span class="sxs-lookup"><span data-stu-id="9c71e-105">For more information on key containers, see [Understanding Machine-Level and User-Level RSA Key Containers](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).</span></span>  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="9c71e-106">Asimetrik anahtar oluşturmak ve bir anahtar kapsayıcısında kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="9c71e-106">To create an asymmetric key and save it in a key container</span></span>  
  
1.  <span data-ttu-id="9c71e-107">Yeni bir örneğini oluşturmak bir <xref:System.Security.Cryptography.CspParameters> sınıfı ve anahtar kapsayıcısı aramak istediğiniz adı <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> alan.</span><span class="sxs-lookup"><span data-stu-id="9c71e-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>  
  
2.  <span data-ttu-id="9c71e-108">Türetilen sınıfın yeni bir örnek oluşturmak <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfı (genellikle **RSACryptoServiceProvider** veya **DSACryptoServiceProvider**) ve daha önce oluşturulmuş geçirin  **CspParameters** kendi oluşturucuya nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9c71e-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
### <a name="to-delete-the-key-from-a-key-container"></a><span data-ttu-id="9c71e-109">Bir anahtar kapsayıcı anahtarını silmek için</span><span class="sxs-lookup"><span data-stu-id="9c71e-109">To delete the key from a key container</span></span>  
  
1.  <span data-ttu-id="9c71e-110">Yeni bir örneğini oluşturmak bir **CspParameters** sınıfı ve anahtar kapsayıcısı aramak istediğiniz adı **CspParameters.KeyContainerName** alan.</span><span class="sxs-lookup"><span data-stu-id="9c71e-110">Create a new instance of a **CspParameters** class and pass the name that you want to call the key container to the **CspParameters.KeyContainerName** field.</span></span>  
  
2.  <span data-ttu-id="9c71e-111">Türetilen sınıfın yeni bir örnek oluşturmak **AsymmetricAlgorithm** sınıfı (genellikle **RSACryptoServiceProvider** veya **DSACryptoServiceProvider**) ve geçirin daha önce oluşturduğunuz **CspParameters** kendi oluşturucuya nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9c71e-111">Create a new instance of a class that derives from the **AsymmetricAlgorithm** class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
3.  <span data-ttu-id="9c71e-112">Ayarlama **PersistKeyInCSP** türetildiği sınıfın özelliği **AsymmetricAlgorithm** için **false** (**False** Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="9c71e-112">Set the **PersistKeyInCSP** property of the class that derives from **AsymmetricAlgorithm** to **false** (**False** in Visual Basic).</span></span>  
  
4.  <span data-ttu-id="9c71e-113">Çağrı **Temizle** yöntemi türetildiği sınıfın **AsymmetricAlgorithm**.</span><span class="sxs-lookup"><span data-stu-id="9c71e-113">Call the **Clear** method of the class that derives from **AsymmetricAlgorithm**.</span></span> <span data-ttu-id="9c71e-114">Bu yöntem sınıfın tüm kaynakları serbest bırakır ve anahtar kapsayıcısı temizler.</span><span class="sxs-lookup"><span data-stu-id="9c71e-114">This method releases all resources of the class and clears the key container.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c71e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c71e-115">Example</span></span>  
 <span data-ttu-id="9c71e-116">Aşağıdaki örnek, bir asimetrik anahtar oluşturmak, bir anahtar kapsayıcısında kaydedin, daha sonraki bir zamanda anahtarı almak ve anahtarı kapsayıcısından silin gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9c71e-116">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>  
  
 <span data-ttu-id="9c71e-117">Bu kodu fark `GenKey_SaveInContainer` yöntemi ve `GetKeyFromContainer` yöntemi benzer.</span><span class="sxs-lookup"><span data-stu-id="9c71e-117">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span>  <span data-ttu-id="9c71e-118">İçin bir anahtar kapsayıcı adı belirttiğinizde bir <xref:System.Security.Cryptography.CspParameters> nesne ve ona geçirin bir <xref:System.Security.Cryptography.AsymmetricAlgorithm> nesnesi ile <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği veya <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği true, şunlar olur ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9c71e-118">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to true, the following occurs.</span></span>  <span data-ttu-id="9c71e-119">Belirtilen ada sahip bir anahtar kapsayıcısı mevcut değilse, ardından oluşturulur ve anahtar kalıcı.</span><span class="sxs-lookup"><span data-stu-id="9c71e-119">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>  <span data-ttu-id="9c71e-120">Belirtilen ada sahip bir anahtar kapsayıcısı yok sonra anahtar kapsayıcısında geçerli otomatik olarak yüklenen <xref:System.Security.Cryptography.AsymmetricAlgorithm> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9c71e-120">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>  <span data-ttu-id="9c71e-121">Bu nedenle, kodda `GenKey_SaveInContainer` yöntemi devam ederse anahtar kodda sırasında ilk çalıştığından `GetKeyFromContainer` yöntemi ikinci çalıştığından anahtarı yükler.</span><span class="sxs-lookup"><span data-stu-id="9c71e-121">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it is run second.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c71e-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c71e-122">See Also</span></span>  
 [<span data-ttu-id="9c71e-123">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c71e-123">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [<span data-ttu-id="9c71e-124">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="9c71e-124">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="9c71e-125">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="9c71e-125">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
 [<span data-ttu-id="9c71e-126">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="9c71e-126">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

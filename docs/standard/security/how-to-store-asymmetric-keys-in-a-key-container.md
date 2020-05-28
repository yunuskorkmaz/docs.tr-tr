---
title: 'Nasıl yapılır: bir anahtar kapsayıcısında asimetrik anahtarlar depolama'
ms.date: 05/26/2020
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
ms.openlocfilehash: 36bae05fbfb35dc112e0c543c9a1a975a8fa8db5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143627"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="4aebc-102">Asimetrik anahtarları bir anahtar kapsayıcısında depola</span><span class="sxs-lookup"><span data-stu-id="4aebc-102">Store asymmetric keys in a key container</span></span>

<span data-ttu-id="4aebc-103">Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4aebc-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="4aebc-104">Özel bir anahtar depolamanız gerekiyorsa, anahtar kapsayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4aebc-104">If you need to store a private key, use a key container.</span></span> <span data-ttu-id="4aebc-105">Anahtar kapsayıcıları hakkında daha fazla bilgi için bkz. [makine düzeyi ve Kullanıcı DÜZEYI RSA anahtar kapsayıcılarını anlama](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4aebc-105">For more information on key containers, see [Understanding machine-level and user-level RSA key containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="4aebc-106">Asimetrik anahtar oluşturma ve anahtar kapsayıcısına kaydetme</span><span class="sxs-lookup"><span data-stu-id="4aebc-106">Create an asymmetric key and save it in a key container</span></span>

1. <span data-ttu-id="4aebc-107">Bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.CspParameters> ve anahtar kapsayıcısını alana çağırmak istediğiniz adı geçirin <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4aebc-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="4aebc-108">Sınıfından (genellikle veya) türetilen bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Security.Cryptography.DSACryptoServiceProvider> ve daha önce oluşturulan `CspParameters` nesneyi yapıcısına geçirin.</span><span class="sxs-lookup"><span data-stu-id="4aebc-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually <xref:System.Security.Cryptography.RSACryptoServiceProvider> or <xref:System.Security.Cryptography.DSACryptoServiceProvider>) and pass the previously created `CspParameters` object to its constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="4aebc-109">Asimetrik anahtarın oluşturulması ve alınması tek bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="4aebc-109">The creation and retrieval of an asymmetric key is one operation.</span></span> <span data-ttu-id="4aebc-110">Bir anahtar kapsayıcıda zaten yoksa, döndürülmeden önce oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4aebc-110">If a key is not already in the container, it's created before being returned.</span></span>
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a><span data-ttu-id="4aebc-111">Anahtarı anahtar kapsayıcısından Sil</span><span class="sxs-lookup"><span data-stu-id="4aebc-111">Delete the key from the key container</span></span>

1. <span data-ttu-id="4aebc-112">Bir sınıfın yeni bir örneğini oluşturun `CspParameters` ve anahtar kapsayıcısını alana çağırmak istediğiniz adı geçirin <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4aebc-112">Create a new instance of a `CspParameters` class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="4aebc-113">Sınıfından (genellikle veya) türetilen bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.AsymmetricAlgorithm> `RSACryptoServiceProvider` `DSACryptoServiceProvider` ve daha önce oluşturulan `CspParameters` nesneyi yapıcısına geçirin.</span><span class="sxs-lookup"><span data-stu-id="4aebc-113">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually `RSACryptoServiceProvider` or `DSACryptoServiceProvider`) and pass the previously created `CspParameters` object to its constructor.</span></span>

1. <span data-ttu-id="4aebc-114">' A <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> `AsymmetricAlgorithm` `false` (Visual Basic) öğesinden türetilen sınıfın özelliğini veya özelliğini ayarlayın `False` .</span><span class="sxs-lookup"><span data-stu-id="4aebc-114">Set the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> or the <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> property of the class that derives from `AsymmetricAlgorithm` to `false` (`False` in Visual Basic).</span></span>

1. <span data-ttu-id="4aebc-115">`Clear`Öğesinden türetilen sınıfın yöntemini çağırın `AsymmetricAlgorithm` .</span><span class="sxs-lookup"><span data-stu-id="4aebc-115">Call the `Clear` method of the class that derives from `AsymmetricAlgorithm`.</span></span> <span data-ttu-id="4aebc-116">Bu yöntem, sınıfın tüm kaynaklarını serbest bırakır ve anahtar kapsayıcısını temizler.</span><span class="sxs-lookup"><span data-stu-id="4aebc-116">This method releases all resources of the class and clears the key container.</span></span>

## <a name="example"></a><span data-ttu-id="4aebc-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="4aebc-117">Example</span></span>

<span data-ttu-id="4aebc-118">Aşağıdaki örnek, asimetrik anahtar oluşturmayı, anahtar kapsayıcısına kaydetmeyi, daha sonra anahtarı almayı ve kapsayıcıyı kapsayıcıdan silmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4aebc-118">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>

<span data-ttu-id="4aebc-119">Yöntemi ve yöntemi içindeki kodun benzer olduğuna dikkat edin `GenKey_SaveInContainer` `GetKeyFromContainer` .</span><span class="sxs-lookup"><span data-stu-id="4aebc-119">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span> <span data-ttu-id="4aebc-120">Bir nesne için bir anahtar kapsayıcı adı belirttiğinizde <xref:System.Security.Cryptography.CspParameters> ve <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği ya da <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği olarak ayarlanmış bir nesneye geçirirseniz `true` , davranış aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="4aebc-120">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to `true`, the behavior is as follows:</span></span>

- <span data-ttu-id="4aebc-121">Belirtilen ada sahip bir anahtar kapsayıcısı yoksa, bir tane oluşturulur ve anahtar kalıcıdır.</span><span class="sxs-lookup"><span data-stu-id="4aebc-121">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>
- <span data-ttu-id="4aebc-122">Belirtilen ada sahip bir anahtar kapsayıcısı varsa, kapsayıcıdaki anahtar geçerli nesneye otomatik olarak yüklenir <xref:System.Security.Cryptography.AsymmetricAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="4aebc-122">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>

<span data-ttu-id="4aebc-123">Bu nedenle, `GenKey_SaveInContainer` ilk olarak çalıştırıldığı için yöntemindeki kod devam ettirir, ancak yöntemin kodu `GetKeyFromContainer` ikinci çalıştırıldığı için anahtarı yükler.</span><span class="sxs-lookup"><span data-stu-id="4aebc-123">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it's run second.</span></span>

```vb
Imports System
Imports System.Security.Cryptography

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

    Private Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        ' name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key added to container:  {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub GetKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key retrieved from container : {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container.
        ' Delete the key entry in the container.
        Dim rsa As New RSACryptoServiceProvider(parameters) With {
            .PersistKeyInCsp = False
        }

        ' Call Clear to release resources and delete the key from the container.
        rsa.Clear()

        Console.WriteLine("Key deleted.")
    End Sub
End Class
```

```csharp
using System;
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
        catch (CryptographicException e)
        {
            Console.WriteLine(e.Message);
        }
    }

    private static void GenKey_SaveInContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key added to container: \n  {rsa.ToXmlString(true)}");
    }

    private static void GetKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key retrieved from container : \n {rsa.ToXmlString(true)}");
    }

    private static void DeleteKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container.
        using var rsa = new RSACryptoServiceProvider(parameters)
        {
            // Delete the key entry in the container.
            PersistKeyInCsp = false
        };

        // Call Clear to release resources and delete the key from the container.
        rsa.Clear();

        Console.WriteLine("Key deleted.");
    }
}
```

<span data-ttu-id="4aebc-124">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="4aebc-124">The output is as follows:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4aebc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aebc-125">See also</span></span>

- [<span data-ttu-id="4aebc-126">Şifreleme ve şifre çözme için anahtarlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="4aebc-126">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="4aebc-127">Verileri şifreleme</span><span class="sxs-lookup"><span data-stu-id="4aebc-127">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="4aebc-128">Verilerin şifresini çözme</span><span class="sxs-lookup"><span data-stu-id="4aebc-128">Decrypting data</span></span>](decrypting-data.md)
- [<span data-ttu-id="4aebc-129">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="4aebc-129">Cryptographic services</span></span>](cryptographic-services.md)

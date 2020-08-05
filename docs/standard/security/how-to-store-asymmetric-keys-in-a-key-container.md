---
title: 'Nasıl yapılır: bir anahtar kapsayıcısında asimetrik anahtarlar depolama'
description: Asimetrik anahtarları .NET 'teki bir anahtar kapsayıcısında depolamayı öğrenin. Asimetrik anahtar oluşturma, anahtar kapsayıcısına kaydetme ve anahtarı alma ve silme bölümüne bakın.
ms.date: 05/26/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET]
- encryption [.NET], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
ms.openlocfilehash: aa6fad815338cbd6316deca7be0a23286630fa56
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556299"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a>Asimetrik anahtarları bir anahtar kapsayıcısında depola

Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır. Özel bir anahtar depolamanız gerekiyorsa, anahtar kapsayıcısı kullanın. Anahtar kapsayıcıları hakkında daha fazla bilgi için bkz. [makine düzeyi ve Kullanıcı DÜZEYI RSA anahtar kapsayıcılarını anlama](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).

> [!NOTE]
> Bu makaledeki kod Windows için geçerlidir.

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Asimetrik anahtar oluşturma ve anahtar kapsayıcısına kaydetme

1. Bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.CspParameters> ve anahtar kapsayıcısını alana çağırmak istediğiniz adı geçirin <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> .

1. Sınıfından (genellikle veya) türetilen bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Security.Cryptography.DSACryptoServiceProvider> ve daha önce oluşturulan `CspParameters` nesneyi yapıcısına geçirin.

> [!NOTE]
> Asimetrik anahtarın oluşturulması ve alınması tek bir işlemdir. Bir anahtar kapsayıcıda zaten yoksa, döndürülmeden önce oluşturulur.
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a>Anahtarı anahtar kapsayıcısından Sil

1. Bir sınıfın yeni bir örneğini oluşturun `CspParameters` ve anahtar kapsayıcısını alana çağırmak istediğiniz adı geçirin <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> .

1. Sınıfından (genellikle veya) türetilen bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.AsymmetricAlgorithm> `RSACryptoServiceProvider` `DSACryptoServiceProvider` ve daha önce oluşturulan `CspParameters` nesneyi yapıcısına geçirin.

1. ' A <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> `AsymmetricAlgorithm` `false` (Visual Basic) öğesinden türetilen sınıfın özelliğini veya özelliğini ayarlayın `False` .

1. `Clear`Öğesinden türetilen sınıfın yöntemini çağırın `AsymmetricAlgorithm` . Bu yöntem, sınıfın tüm kaynaklarını serbest bırakır ve anahtar kapsayıcısını temizler.

## <a name="example"></a>Örnek

Aşağıdaki örnek, asimetrik anahtar oluşturmayı, anahtar kapsayıcısına kaydetmeyi, daha sonra anahtarı almayı ve kapsayıcıyı kapsayıcıdan silmeyi gösterir.

Yöntemi ve yöntemi içindeki kodun benzer olduğuna dikkat edin `GenKey_SaveInContainer` `GetKeyFromContainer` . Bir nesne için bir anahtar kapsayıcı adı belirttiğinizde <xref:System.Security.Cryptography.CspParameters> ve <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği ya da <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> özelliği olarak ayarlanmış bir nesneye geçirirseniz `true` , davranış aşağıdaki gibidir:

- Belirtilen ada sahip bir anahtar kapsayıcısı yoksa, bir tane oluşturulur ve anahtar kalıcıdır.
- Belirtilen ada sahip bir anahtar kapsayıcısı varsa, kapsayıcıdaki anahtar geçerli nesneye otomatik olarak yüklenir <xref:System.Security.Cryptography.AsymmetricAlgorithm> .

Bu nedenle, `GenKey_SaveInContainer` ilk olarak çalıştırıldığı için yöntemindeki kod devam ettirir, ancak yöntemin kodu `GetKeyFromContainer` ikinci çalıştırıldığı için anahtarı yükler.

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

Çıktı aşağıdaki şekilde olacaktır:

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

- [Şifreleme Modeli](cryptography-model.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [Şifreleme ve şifre çözme için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md)
- [Verileri şifreleme](encrypting-data.md)
- [Verilerin şifresini çözme](decrypting-data.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

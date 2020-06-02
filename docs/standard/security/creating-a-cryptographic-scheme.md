---
title: Şifreleme Düzeni Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288426"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="106bc-102">Şifreleme Düzeni Oluşturma</span><span class="sxs-lookup"><span data-stu-id="106bc-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="106bc-103">.NET Framework şifreleme bileşenleri, verileri şifrelemek ve şifrelerini çözmek için farklı şemalar oluşturmak üzere birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="106bc-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="106bc-104">Verileri şifrelemek ve şifrelerini çözmek için basit bir şifreleme şeması aşağıdaki adımları belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="106bc-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1. <span data-ttu-id="106bc-105">Her taraf ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="106bc-105">Each party generates a public/private key pair.</span></span>  
  
2. <span data-ttu-id="106bc-106">Taraflar ortak anahtarlarını değiş tokuş altına alırlar.</span><span class="sxs-lookup"><span data-stu-id="106bc-106">The parties exchange their public keys.</span></span>  
  
3. <span data-ttu-id="106bc-107">Her bir taraf, üç aylık şifreleme için gizli bir anahtar oluşturur, örneğin, diğer ortak anahtarını kullanarak yeni oluşturulan anahtarı şifreler.</span><span class="sxs-lookup"><span data-stu-id="106bc-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4. <span data-ttu-id="106bc-108">Her bir taraf, verileri birbirlerine gönderir ve yeni bir gizli anahtar oluşturmak için kendi gizli anahtarını belirli bir sırada kendi kendine birleştirir.</span><span class="sxs-lookup"><span data-stu-id="106bc-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5. <span data-ttu-id="106bc-109">Taraflar daha sonra simetrik şifrelemeyi kullanarak bir konuşma başlatır.</span><span class="sxs-lookup"><span data-stu-id="106bc-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="106bc-110">Şifreleme düzeni oluşturmak, önemsiz bir görev değildir.</span><span class="sxs-lookup"><span data-stu-id="106bc-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="106bc-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="106bc-111">See also</span></span>

- [<span data-ttu-id="106bc-112">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="106bc-112">Cryptographic Services</span></span>](cryptographic-services.md)

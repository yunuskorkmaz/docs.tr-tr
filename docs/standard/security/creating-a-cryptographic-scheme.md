---
title: Şifreleme Düzeni Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2db6d4229ac777801aff792c86fe0e5e9a1b4994
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031701"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="a0608-102">Şifreleme Düzeni Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0608-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="a0608-103">.NET Framework şifreleme bileşenlerini şifrelemek ve verilerin şifresini çözmek için farklı düzenleri oluşturmak için birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a0608-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="a0608-104">Şifreleme ve verilerin şifresini çözmek için basit bir şifreleme düzeni aşağıdakileri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a0608-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="a0608-105">Her iki taraf bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0608-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="a0608-106">Taraflar, ortak anahtar değişimi.</span><span class="sxs-lookup"><span data-stu-id="a0608-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="a0608-107">Her iki taraf TripleDES şifreleme için gizli bir anahtar oluşturur ve diğer kişinin ortak anahtar kullanarak yeni oluşturulan anahtarı şifreler.</span><span class="sxs-lookup"><span data-stu-id="a0608-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="a0608-108">Her bir taraf, diğer veri gönderir ve yeni bir gizli anahtar oluşturmak için kendi belirli bir siparişi ile diğer tarafın gizli anahtar birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a0608-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="a0608-109">Taraflar ardından simetrik şifreleme kullanarak bir konuşma başlatır.</span><span class="sxs-lookup"><span data-stu-id="a0608-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="a0608-110">Şifreleme düzeni oluşturma, basit bir görev değildir.</span><span class="sxs-lookup"><span data-stu-id="a0608-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="a0608-111">Şifreleme kullanarak daha fazla bilgi için Platform SDK belgelerine şifreleme bölümüne bakın. http://msdn.microsoft.com/library.</span><span class="sxs-lookup"><span data-stu-id="a0608-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0608-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0608-112">See also</span></span>

- [<span data-ttu-id="a0608-113">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="a0608-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

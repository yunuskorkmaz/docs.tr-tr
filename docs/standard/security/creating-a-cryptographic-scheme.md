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
ms.openlocfilehash: 3ef3741ef5cec720c2fb285c9aa60d610acc0be9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321659"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="e10e8-102">Şifreleme Düzeni Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e10e8-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="e10e8-103">.NET Framework şifreleme bileşenlerini şifrelemek ve verilerin şifresini çözmek için farklı düzenleri oluşturmak için birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e10e8-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="e10e8-104">Şifreleme ve verilerin şifresini çözmek için basit bir şifreleme düzeni aşağıdakileri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e10e8-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1. <span data-ttu-id="e10e8-105">Her iki taraf bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e10e8-105">Each party generates a public/private key pair.</span></span>  
  
2. <span data-ttu-id="e10e8-106">Taraflar, ortak anahtar değişimi.</span><span class="sxs-lookup"><span data-stu-id="e10e8-106">The parties exchange their public keys.</span></span>  
  
3. <span data-ttu-id="e10e8-107">Her iki taraf TripleDES şifreleme için gizli bir anahtar oluşturur ve diğer kişinin ortak anahtar kullanarak yeni oluşturulan anahtarı şifreler.</span><span class="sxs-lookup"><span data-stu-id="e10e8-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4. <span data-ttu-id="e10e8-108">Her bir taraf, diğer veri gönderir ve yeni bir gizli anahtar oluşturmak için kendi belirli bir siparişi ile diğer tarafın gizli anahtar birleştirir.</span><span class="sxs-lookup"><span data-stu-id="e10e8-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5. <span data-ttu-id="e10e8-109">Taraflar ardından simetrik şifreleme kullanarak bir konuşma başlatır.</span><span class="sxs-lookup"><span data-stu-id="e10e8-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="e10e8-110">Şifreleme düzeni oluşturma, basit bir görev değildir.</span><span class="sxs-lookup"><span data-stu-id="e10e8-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e10e8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e10e8-111">See also</span></span>

- [<span data-ttu-id="e10e8-112">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e10e8-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

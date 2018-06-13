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
ms.openlocfilehash: b1635276465dd58028c8a5e4b7e69a307664a4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580763"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="41e0c-102">Şifreleme Düzeni Oluşturma</span><span class="sxs-lookup"><span data-stu-id="41e0c-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="41e0c-103">.NET Framework şifreleme bileşenlerinin şifrelemek ve verilerin şifresini çözmek için farklı düzenleri oluşturmak için birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="41e0c-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="41e0c-104">Şifreleme ve verilerin şifresini çözmek için basit bir şifreleme şeması aşağıdakileri belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="41e0c-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="41e0c-105">Her taraf ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41e0c-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="41e0c-106">Tarafların sitelerin genel anahtarlarını exchange.</span><span class="sxs-lookup"><span data-stu-id="41e0c-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="41e0c-107">Her taraf TripleDES şifreleme için gizli bir anahtar oluşturur örneğin ve diğer kişilerin ortak anahtar kullanarak yeni oluşturulan anahtarı şifreler.</span><span class="sxs-lookup"><span data-stu-id="41e0c-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="41e0c-108">Her taraf diğer verileri gönderir ve diğer kişilerin gizli anahtarı yeni gizli bir anahtar oluşturmak için kendi belirli bir sıra ile birleştirir.</span><span class="sxs-lookup"><span data-stu-id="41e0c-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="41e0c-109">Taraflar ardından simetrik şifreleme kullanarak bir konuşma başlatın.</span><span class="sxs-lookup"><span data-stu-id="41e0c-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="41e0c-110">Şifreleme düzeni oluşturma, karmaşık bir görev değil.</span><span class="sxs-lookup"><span data-stu-id="41e0c-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="41e0c-111">Şifreleme kullanma hakkında daha fazla bilgi için Platform SDK belgelerine şifreleme konusuna bakın http://msdn.microsoft.com/library.</span><span class="sxs-lookup"><span data-stu-id="41e0c-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e0c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41e0c-112">See Also</span></span>  
 [<span data-ttu-id="41e0c-113">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="41e0c-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

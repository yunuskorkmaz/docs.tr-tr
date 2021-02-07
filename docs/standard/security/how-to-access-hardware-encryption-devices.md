---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: donanım şifreleme cihazlarına erişme'
title: 'Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: fcf12314490542848d20bd3a4977d68c386853bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685276"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="855cb-103">Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim</span><span class="sxs-lookup"><span data-stu-id="855cb-103">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="855cb-104">Bu makale Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="855cb-104">This article applies to Windows.</span></span>

<span data-ttu-id="855cb-105"><xref:System.Security.Cryptography.CspParameters>Donanım şifreleme cihazlarına erişmek için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="855cb-105">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="855cb-106">Örneğin, uygulamanızı bir akıllı kart, donanım rastgele numara Oluşturucu veya belirli bir şifreleme algoritmasının donanım uygulamasıyla bütünleştirmek için bu sınıfı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="855cb-106">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="855cb-107"><xref:System.Security.Cryptography.CspParameters>Sınıfı, düzgün yüklenmiş bir donanım şifreleme cihazına erişen bir şifreleme hizmeti sağlayıcısı (CSP) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="855cb-107">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="855cb-108">CSP 'nin kullanılabilirliğini, kayıt defteri Düzenleyicisi (Regedit.exe) kullanarak aşağıdaki kayıt defteri anahtarını inceleyerek doğrulayabilirsiniz: HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="855cb-108">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="855cb-109">Bir anahtar kartı kullanarak verileri imzalamak için</span><span class="sxs-lookup"><span data-stu-id="855cb-109">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="855cb-110">Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.CspParameters> , tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="855cb-110">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="855cb-111"><xref:System.Security.Cryptography.CspParameters.Flags%2A>Yeni oluşturulan nesnenin özelliğine uygun bayrakları geçirin <xref:System.Security.Cryptography.CspParameters> .</span><span class="sxs-lookup"><span data-stu-id="855cb-111">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="855cb-112">Örneğin, <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> bayrağını geçirin.</span><span class="sxs-lookup"><span data-stu-id="855cb-112">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="855cb-113">Bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.AsymmetricAlgorithm> (örneğin, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı), <xref:System.Security.Cryptography.CspParameters> nesneyi oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="855cb-113">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="855cb-114">Yöntemlerden birini kullanarak verilerinizi imzalayın `Sign` ve yöntemlerden birini kullanarak verilerinizi doğrulayın `Verify` .</span><span class="sxs-lookup"><span data-stu-id="855cb-114">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="855cb-115">Donanım rastgele numara Oluşturucu kullanarak rastgele bir sayı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="855cb-115">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="855cb-116">Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.CspParameters> , tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="855cb-116">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="855cb-117">Nesnesini oluşturucuya geçirerek yeni bir örneğini oluşturun <xref:System.Security.Cryptography.RNGCryptoServiceProvider> <xref:System.Security.Cryptography.CspParameters> .</span><span class="sxs-lookup"><span data-stu-id="855cb-117">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="855cb-118">Veya yöntemini kullanarak rastgele bir değer <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> oluşturun <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> .</span><span class="sxs-lookup"><span data-stu-id="855cb-118">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="855cb-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="855cb-119">Example</span></span>

<span data-ttu-id="855cb-120">Aşağıdaki kod örneği, bir akıllı kart kullanılarak verilerin nasıl imzalanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="855cb-120">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="855cb-121">Kod örneği <xref:System.Security.Cryptography.CspParameters> , akıllı kart sunan bir nesne oluşturur ve ardından <xref:System.Security.Cryptography.RSACryptoServiceProvider> CSP kullanarak bir nesneyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="855cb-121">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="855cb-122">Kod örneği daha sonra bazı verileri imzalar ve doğrular.</span><span class="sxs-lookup"><span data-stu-id="855cb-122">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="855cb-123">SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneririz.</span><span class="sxs-lookup"><span data-stu-id="855cb-123">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="855cb-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="855cb-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="855cb-125"><xref:System>Ve <xref:System.Security.Cryptography> ad alanlarını dahil edin.</span><span class="sxs-lookup"><span data-stu-id="855cb-125">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="855cb-126">Bilgisayarınızda yüklü bir akıllı kart okuyucunuz ve sürücüleriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="855cb-126">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="855cb-127"><xref:System.Security.Cryptography.CspParameters>Kartını, kart okuyucunuzun özel bilgilerini kullanarak başlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="855cb-127">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="855cb-128">Daha fazla bilgi için, kart okuyucunuzun belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="855cb-128">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="855cb-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="855cb-129">See also</span></span>

- [<span data-ttu-id="855cb-130">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="855cb-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="855cb-131">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="855cb-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="855cb-132">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="855cb-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="855cb-133">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="855cb-133">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

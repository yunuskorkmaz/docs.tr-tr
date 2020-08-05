---
title: 'Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim'
ms.date: 07/14/2020
ms.technology: dotnet-standard
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
ms.openlocfilehash: 7cd3aab80a8388c1d4ce08e4ae94aae84cfff239
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557144"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="62a1a-102">Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim</span><span class="sxs-lookup"><span data-stu-id="62a1a-102">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="62a1a-103">Bu makale Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="62a1a-103">This article applies to Windows.</span></span>

<span data-ttu-id="62a1a-104"><xref:System.Security.Cryptography.CspParameters>Donanım şifreleme cihazlarına erişmek için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62a1a-104">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="62a1a-105">Örneğin, uygulamanızı bir akıllı kart, donanım rastgele numara Oluşturucu veya belirli bir şifreleme algoritmasının donanım uygulamasıyla bütünleştirmek için bu sınıfı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62a1a-105">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="62a1a-106"><xref:System.Security.Cryptography.CspParameters>Sınıfı, düzgün yüklenmiş bir donanım şifreleme cihazına erişen bir şifreleme hizmeti sağlayıcısı (CSP) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62a1a-106">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="62a1a-107">CSP 'nin kullanılabilirliğini, kayıt defteri düzenleyicisini (Regedit.exe) kullanarak aşağıdaki kayıt defteri anahtarını inceleyerek doğrulayabilirsiniz: HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="62a1a-107">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="62a1a-108">Bir anahtar kartı kullanarak verileri imzalamak için</span><span class="sxs-lookup"><span data-stu-id="62a1a-108">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="62a1a-109">Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.CspParameters> , tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="62a1a-109">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="62a1a-110"><xref:System.Security.Cryptography.CspParameters.Flags%2A>Yeni oluşturulan nesnenin özelliğine uygun bayrakları geçirin <xref:System.Security.Cryptography.CspParameters> .</span><span class="sxs-lookup"><span data-stu-id="62a1a-110">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="62a1a-111">Örneğin, <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> bayrağını geçirin.</span><span class="sxs-lookup"><span data-stu-id="62a1a-111">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="62a1a-112">Bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.AsymmetricAlgorithm> (örneğin, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı), <xref:System.Security.Cryptography.CspParameters> nesneyi oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="62a1a-112">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="62a1a-113">Yöntemlerden birini kullanarak verilerinizi imzalayın `Sign` ve yöntemlerden birini kullanarak verilerinizi doğrulayın `Verify` .</span><span class="sxs-lookup"><span data-stu-id="62a1a-113">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="62a1a-114">Donanım rastgele numara Oluşturucu kullanarak rastgele bir sayı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="62a1a-114">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="62a1a-115">Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.CspParameters> , tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="62a1a-115">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="62a1a-116">Nesnesini oluşturucuya geçirerek yeni bir örneğini oluşturun <xref:System.Security.Cryptography.RNGCryptoServiceProvider> <xref:System.Security.Cryptography.CspParameters> .</span><span class="sxs-lookup"><span data-stu-id="62a1a-116">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="62a1a-117">Veya yöntemini kullanarak rastgele bir değer <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> oluşturun <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> .</span><span class="sxs-lookup"><span data-stu-id="62a1a-117">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62a1a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="62a1a-118">Example</span></span>

<span data-ttu-id="62a1a-119">Aşağıdaki kod örneği, bir akıllı kart kullanılarak verilerin nasıl imzalanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="62a1a-119">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="62a1a-120">Kod örneği <xref:System.Security.Cryptography.CspParameters> , akıllı kart sunan bir nesne oluşturur ve ardından <xref:System.Security.Cryptography.RSACryptoServiceProvider> CSP kullanarak bir nesneyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="62a1a-120">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="62a1a-121">Kod örneği daha sonra bazı verileri imzalar ve doğrular.</span><span class="sxs-lookup"><span data-stu-id="62a1a-121">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="62a1a-122">SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneririz.</span><span class="sxs-lookup"><span data-stu-id="62a1a-122">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62a1a-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="62a1a-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="62a1a-124"><xref:System>Ve <xref:System.Security.Cryptography> ad alanlarını dahil edin.</span><span class="sxs-lookup"><span data-stu-id="62a1a-124">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="62a1a-125">Bilgisayarınızda yüklü bir akıllı kart okuyucunuz ve sürücüleriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62a1a-125">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="62a1a-126"><xref:System.Security.Cryptography.CspParameters>Kartını, kart okuyucunuzun özel bilgilerini kullanarak başlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="62a1a-126">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="62a1a-127">Daha fazla bilgi için, kart okuyucunuzun belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="62a1a-127">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="62a1a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62a1a-128">See also</span></span>

- [<span data-ttu-id="62a1a-129">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="62a1a-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="62a1a-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="62a1a-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="62a1a-131">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="62a1a-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="62a1a-132">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="62a1a-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

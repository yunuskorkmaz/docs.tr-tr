---
title: 'Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim'
ms.date: 03/30/2017
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
ms.openlocfilehash: d6ee22fd9fb0c11e22ac01ff83b3269e37e37763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706181"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="6d821-102">Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim</span><span class="sxs-lookup"><span data-stu-id="6d821-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="6d821-103">Donanım şifreleme cihazlarına erişmek için <xref:System.Security.Cryptography.CspParameters> sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d821-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="6d821-104">Örneğin, uygulamanızı bir akıllı kart, donanım rastgele numara Oluşturucu veya belirli bir şifreleme algoritmasının donanım uygulamasıyla bütünleştirmek için bu sınıfı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d821-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="6d821-105"><xref:System.Security.Cryptography.CspParameters> sınıfı, düzgün yüklenmiş bir donanım şifreleme cihazına erişen bir şifreleme hizmeti sağlayıcısı (CSP) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d821-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="6d821-106">CSP 'nin kullanılabilirliğini, kayıt defteri Düzenleyicisi 'Ni (Regedit. exe) kullanarak aşağıdaki kayıt defteri anahtarını inceleyerek doğrulayabilirsiniz: HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="6d821-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="6d821-107">Bir anahtar kartı kullanarak verileri imzalamak için</span><span class="sxs-lookup"><span data-stu-id="6d821-107">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="6d821-108"><xref:System.Security.Cryptography.CspParameters> sınıfının yeni bir örneğini oluşturun, tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="6d821-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="6d821-109">Uygun bayrakları yeni oluşturulan <xref:System.Security.Cryptography.CspParameters> nesnesinin <xref:System.Security.Cryptography.CspParameters.Flags%2A> özelliğine geçirin.</span><span class="sxs-lookup"><span data-stu-id="6d821-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="6d821-110">Örneğin <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> bayrağını geçirin.</span><span class="sxs-lookup"><span data-stu-id="6d821-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="6d821-111"><xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfının yeni bir örneğini oluşturun (örneğin, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı), <xref:System.Security.Cryptography.CspParameters> nesnesini oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="6d821-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="6d821-112">`Sign` yöntemlerinden birini kullanarak verilerinizi imzalayın ve `Verify` yöntemlerinden birini kullanarak verilerinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6d821-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="6d821-113">Donanım rastgele numara Oluşturucu kullanarak rastgele bir sayı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6d821-113">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="6d821-114"><xref:System.Security.Cryptography.CspParameters> sınıfının yeni bir örneğini oluşturun, tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.</span><span class="sxs-lookup"><span data-stu-id="6d821-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="6d821-115"><xref:System.Security.Cryptography.CspParameters> nesnesini oluşturucuya geçirerek <xref:System.Security.Cryptography.RNGCryptoServiceProvider>yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d821-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="6d821-116"><xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> veya <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> yöntemini kullanarak rastgele bir değer oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d821-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d821-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d821-117">Example</span></span>  
 <span data-ttu-id="6d821-118">Aşağıdaki kod örneği, bir akıllı kart kullanılarak verilerin nasıl imzalanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6d821-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="6d821-119">Kod örneği, akıllı kartı kullanıma sunan bir <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturur ve sonra CSP kullanarak bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi başlatır.</span><span class="sxs-lookup"><span data-stu-id="6d821-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="6d821-120">Kod örneği daha sonra bazı verileri imzalar ve doğrular.</span><span class="sxs-lookup"><span data-stu-id="6d821-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d821-121">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="6d821-121">Compiling the Code</span></span>  
  
- <span data-ttu-id="6d821-122"><xref:System> ve <xref:System.Security.Cryptography> ad alanlarını dahil edin.</span><span class="sxs-lookup"><span data-stu-id="6d821-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="6d821-123">Bilgisayarınızda yüklü bir akıllı kart okuyucunuz ve sürücüleriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6d821-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="6d821-124"><xref:System.Security.Cryptography.CspParameters> nesnesini, kart okuyucunuzun özel bilgilerini kullanarak başlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="6d821-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="6d821-125">Daha fazla bilgi için, kart okuyucunuzun belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="6d821-125">For more information, see the documentation of your card reader.</span></span>

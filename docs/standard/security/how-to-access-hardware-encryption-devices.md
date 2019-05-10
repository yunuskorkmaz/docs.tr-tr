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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c16c994e3976fb3ee569799461db1d1789a6186
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654375"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="227a9-102">Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim</span><span class="sxs-lookup"><span data-stu-id="227a9-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="227a9-103">Kullanabileceğiniz <xref:System.Security.Cryptography.CspParameters> donanım şifreleme cihazlarına erişim için sınıf.</span><span class="sxs-lookup"><span data-stu-id="227a9-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="227a9-104">Örneğin, bu sınıf, uygulamanızın bir akıllı kart, donanım rastgele sayı üretici veya belirli bir şifreleme algoritması bir donanım uygulaması ile tümleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="227a9-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="227a9-105"><xref:System.Security.Cryptography.CspParameters> Sınıfı yüklendiğinden donanım şifreleme cihaz erişen bir şifreleme hizmeti sağlayıcısı (CSP) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="227a9-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="227a9-106">Kayıt Defteri Düzenleyicisi'ni (Regedit.exe) kullanarak aşağıdaki kayıt defteri anahtarını inceleyerek bir CSP kullanılabilirliğini doğrulayabilirsiniz:  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="227a9-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="227a9-107">Anahtar kartı kullanarak verileri imzalamak için</span><span class="sxs-lookup"><span data-stu-id="227a9-107">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="227a9-108">Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.CspParameters> tamsayı sağlayıcı türünü ve sağlayıcı adı oluşturucusuna geçirerek sınıfı.</span><span class="sxs-lookup"><span data-stu-id="227a9-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="227a9-109">Geçirmek için uygun bayrakları <xref:System.Security.Cryptography.CspParameters.Flags%2A> özelliği yeni oluşturulan <xref:System.Security.Cryptography.CspParameters> nesne.</span><span class="sxs-lookup"><span data-stu-id="227a9-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="227a9-110">Örneğin, <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> bayrağı.</span><span class="sxs-lookup"><span data-stu-id="227a9-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="227a9-111">Yeni bir örneğini oluşturmak bir <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfı (örneğin, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı), geçen <xref:System.Security.Cryptography.CspParameters> oluşturucusuna.</span><span class="sxs-lookup"><span data-stu-id="227a9-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="227a9-112">Verilerinizi kullanarak oturum `Sign` yöntemlerden birini kullanarak verilerinizi doğrulayın `Verify` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="227a9-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="227a9-113">Bir donanım rastgele sayı oluşturucusunu kullanarak rastgele bir sayı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="227a9-113">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="227a9-114">Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.CspParameters> tamsayı sağlayıcı türünü ve sağlayıcı adı oluşturucusuna geçirerek sınıfı.</span><span class="sxs-lookup"><span data-stu-id="227a9-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="227a9-115">Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, geçen <xref:System.Security.Cryptography.CspParameters> oluşturucusuna.</span><span class="sxs-lookup"><span data-stu-id="227a9-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="227a9-116">Bir rastgele bir değer kullanarak oluşturduğunuz <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> veya <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="227a9-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="227a9-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="227a9-117">Example</span></span>  
 <span data-ttu-id="227a9-118">Aşağıdaki kod örneği, bir akıllı kart kullanarak verileri imzalamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="227a9-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="227a9-119">Kod örneği oluşturur bir <xref:System.Security.Cryptography.CspParameters> bir akıllı kart kullanıma sunar ve ardından başlatır nesne bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> CSP kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="227a9-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="227a9-120">Kod örneği sonra imzalar ve bazı verileri doğrular.</span><span class="sxs-lookup"><span data-stu-id="227a9-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="227a9-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="227a9-121">Compiling the Code</span></span>  
  
- <span data-ttu-id="227a9-122">Dahil <xref:System> ve <xref:System.Security.Cryptography> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="227a9-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="227a9-123">Bir akıllı kart okuyucu ve sürücüleri yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="227a9-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="227a9-124">Başlatması gerekir <xref:System.Security.Cryptography.CspParameters> kart okuyucu için belirli bilgileri kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="227a9-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="227a9-125">Daha fazla bilgi için kart okuyucusu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="227a9-125">For more information, see the documentation of your card reader.</span></span>

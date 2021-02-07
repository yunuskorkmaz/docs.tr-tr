---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: aynı türde birden fazla güvenlik belirteci kullanma'
title: 'Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 0cbf831c82fdc2aee5a09237c586286a5776d234
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734262"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="2e3cb-103">Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma</span><span class="sxs-lookup"><span data-stu-id="2e3cb-103">How to: Use Multiple Security Tokens of the Same Type</span></span>

- <span data-ttu-id="2e3cb-104">.NET Framework 3,0 ' de, istemci iletisi yalnızca belirli bir türün bir belirtecini içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-104">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="2e3cb-105">Artık istemci iletileri bir tür için birden çok belirteç içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-105">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="2e3cb-106">Bu konu başlığında, istemci iletisinde aynı türde birden fazla belirteç ekleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-106">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="2e3cb-107">Hizmeti bu şekilde yapılandıramayacağınızı unutmayın: bir hizmet yalnızca bir destekleme belirteci içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-107">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="2e3cb-108">Aynı türde birden fazla güvenlik belirteci kullanmak için</span><span class="sxs-lookup"><span data-stu-id="2e3cb-108">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="2e3cb-109">Doldurulacak boş bir bağlama öğesi koleksiyonu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-109">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="2e3cb-110">Çağırarak oluşturun <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="2e3cb-110">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="2e3cb-111">Koleksiyon oluşturun <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> .</span><span class="sxs-lookup"><span data-stu-id="2e3cb-111">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="2e3cb-112">Koleksiyona SAML belirteçleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-112">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="2e3cb-113">Koleksiyonunu öğesine ekleyin <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="2e3cb-113">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="2e3cb-114">Bağlama öğesi koleksiyonuna bağlama öğeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-114">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="2e3cb-115">Bağlama öğesi koleksiyonundan oluşturulan yeni bir özel bağlama döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-115">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="2e3cb-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e3cb-116">Example</span></span>  

 <span data-ttu-id="2e3cb-117">Aşağıda, önceki yordamda açıklanan yöntemin tamamı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-117">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  

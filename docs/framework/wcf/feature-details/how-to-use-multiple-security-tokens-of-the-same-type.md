---
title: 'Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
author: BrucePerlerMS
ms.openlocfilehash: 9d1dab0f4da82e4db96471f0a8cf25c32bd5eced
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198923"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="8cd17-102">Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma</span><span class="sxs-lookup"><span data-stu-id="8cd17-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="8cd17-103">İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, belirtilen her türlü istemci iletisi yalnızca kapsanan bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="8cd17-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="8cd17-104">Artık istemci iletileri birden çok belirteç türü içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8cd17-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="8cd17-105">Bu konuda, bir istemci iletiye aynı türde birden çok belirteç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8cd17-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="8cd17-106">Bu şekilde bir hizmet yapılandıramazsınız Not: hizmet yalnızca bir destekleme belirteci içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8cd17-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="8cd17-107">Aynı türde birden fazla belirteç kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8cd17-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="8cd17-108">Doldurulacak bir boş bağlama öğesi koleksiyonu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8cd17-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="8cd17-109">Oluşturma bir <xref:System.ServiceModel.Channels.SecurityBindingElement> çağırarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="8cd17-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="8cd17-110">Oluşturma bir <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8cd17-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="8cd17-111">SAML belirteçlerini koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8cd17-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="8cd17-112">Koleksiyona ekleme <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="8cd17-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="8cd17-113">Bağlama öğeleri bağlama öğesi koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8cd17-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="8cd17-114">Bağlama öğesi koleksiyonundan oluşturulan yeni bir özel bağlama döndürür.</span><span class="sxs-lookup"><span data-stu-id="8cd17-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="8cd17-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8cd17-115">Example</span></span>  
 <span data-ttu-id="8cd17-116">Yukarıdaki yordamı tarafından tanımlanan tüm yöntemi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8cd17-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="8cd17-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8cd17-117">See Also</span></span>  
 [<span data-ttu-id="8cd17-118">Güvenlik mimarisi</span><span class="sxs-lookup"><span data-stu-id="8cd17-118">Security Architecture</span></span>](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)

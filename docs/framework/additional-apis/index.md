---
title: "Ek sınıf kitaplıkları ve API'leri"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3bb7a7c53cbca8bbd4026b46ce59589cef22382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="e974b-102">Ek sınıf kitaplıkları ve API'leri</span><span class="sxs-lookup"><span data-stu-id="e974b-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="e974b-103">.NET Framework sürekli gelişen ve platformlar arası geliştirme geliştirmek için veya yeni işlevsellik erken müşterilerimizin tanıtmak için şu yeni özellikler bant dışı (OOB) dışında bırakın.</span><span class="sxs-lookup"><span data-stu-id="e974b-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="e974b-104">Bu konuda belgelerine sağladığımız OOB projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="e974b-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="e974b-105">Ayrıca, bazı kitaplıklar belirli platformlar veya .NET Framework uygulamaları hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="e974b-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="e974b-106">Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıfı kod sayfası Kodlamalar .NET Framework kullanılarak geliştirilmiş UWP uygulamaları için kullanılabilir yapar.</span><span class="sxs-lookup"><span data-stu-id="e974b-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="e974b-107">Bu konuda Bu kitaplıklar de listelenir.</span><span class="sxs-lookup"><span data-stu-id="e974b-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="e974b-108">OOB projeleri</span><span class="sxs-lookup"><span data-stu-id="e974b-108">OOB projects</span></span>
  
| <span data-ttu-id="e974b-109">Project</span><span class="sxs-lookup"><span data-stu-id="e974b-109">Project</span></span> | <span data-ttu-id="e974b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e974b-110">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="e974b-111">İş parçacığı güvenli ve hiçbir zaman içeriklerini değiştirmek için garantili olan koleksiyonları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e974b-111">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="e974b-112">Bir ileti işleyicisi sağlar <xref:System.Net.Http.HttpClient> Windows WinHTTP arabirimi esas alan.</span><span class="sxs-lookup"><span data-stu-id="e974b-112">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="e974b-113">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="e974b-113">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="e974b-114">Bir kitaplık SIMD donanım tabanlı hızlandırma yararlanabilir vektör türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e974b-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="e974b-115">TPL veri akışı kitaplığı eşzamanlılık özellikli uygulamalar'ların sağlamlığını artırmak için veri akışı bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e974b-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="e974b-116">Platforma özgü kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="e974b-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="e974b-117">Project</span><span class="sxs-lookup"><span data-stu-id="e974b-117">Project</span></span> | <span data-ttu-id="e974b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e974b-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="e974b-119">Genişletir <xref:System.Text.EncodingProvider> kod sayfası Kodlamalar Evrensel Windows platformu hedefleyen uygulamalar kullanılabilir hale getirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e974b-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="e974b-120">Özel API'leri</span><span class="sxs-lookup"><span data-stu-id="e974b-120">Private APIs</span></span>  

<span data-ttu-id="e974b-121">Bu API ürün altyapısını destekleyen ve amaçlanan/desteklenen doğrudan kodunuzdan kullanılmak üzere değildir.</span><span class="sxs-lookup"><span data-stu-id="e974b-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="e974b-122">API adı</span><span class="sxs-lookup"><span data-stu-id="e974b-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="e974b-123">System.Net.Connection sınıfı</span><span class="sxs-lookup"><span data-stu-id="e974b-123">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="e974b-124">System.Net.Connection.m\_WriteList alan</span><span class="sxs-lookup"><span data-stu-id="e974b-124">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="e974b-125">System.Net.ConnectionGroup sınıfı</span><span class="sxs-lookup"><span data-stu-id="e974b-125">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="e974b-126">System.Net.ConnectionGroup.m\_ConnectionList alan</span><span class="sxs-lookup"><span data-stu-id="e974b-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="e974b-127">System.Net.HttpWebRequest. \_HttpResponse alan</span><span class="sxs-lookup"><span data-stu-id="e974b-127">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="e974b-128">System.Net.HttpWebRequest. \_AutoRedirects alan</span><span class="sxs-lookup"><span data-stu-id="e974b-128">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="e974b-129">System.Net.ServicePoint.m\_ConnectionGroupList alan</span><span class="sxs-lookup"><span data-stu-id="e974b-129">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="e974b-130">System.Net.ServicePointManager.s\_ServicePointTable alan</span><span class="sxs-lookup"><span data-stu-id="e974b-130">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="e974b-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes alan</span><span class="sxs-lookup"><span data-stu-id="e974b-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="e974b-132">System.Windows.Forms.Design.DataMemberFieldEditor sınıfı</span><span class="sxs-lookup"><span data-stu-id="e974b-132">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="e974b-133">System.Windows.Forms.Design.DataMemberListEditor sınıfı</span><span class="sxs-lookup"><span data-stu-id="e974b-133">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="e974b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e974b-134">See also</span></span>

[<span data-ttu-id="e974b-135">.NET Framework ve bant dışı yayınlar</span><span class="sxs-lookup"><span data-stu-id="e974b-135">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

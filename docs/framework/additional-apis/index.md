---
title: Ek sınıf kitaplıkları ve API'ler
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 7659dde4a2cb08fc3257d2f613ce4146522072b6
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478876"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="55893-102">Ek sınıf kitaplıkları ve API'ler</span><span class="sxs-lookup"><span data-stu-id="55893-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="55893-103">.NET Framework sürekli gelişmektedir.</span><span class="sxs-lookup"><span data-stu-id="55893-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="55893-104">Platformlar arası geliştirmeyi geliştirmek ve erken yeni işlevleri tanıtmak için yeni özellikleri bant dışında (OOB) yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="55893-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="55893-105">Bu konuda size sağladığımız belgeleri için OOB projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="55893-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="55893-106">Ayrıca, bazı kitaplıklar belirli platformlara veya .NET Framework uygulamaları hedefler.</span><span class="sxs-lookup"><span data-stu-id="55893-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="55893-107">Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıfı kod sayfası kodlamaları için UWP uygulamaları .NET Framework kullanılarak geliştirilmiş kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="55893-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="55893-108">Bu konuda, bu kitaplıkların da listelenir.</span><span class="sxs-lookup"><span data-stu-id="55893-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="55893-109">OOB projeleri</span><span class="sxs-lookup"><span data-stu-id="55893-109">OOB projects</span></span>
  
| <span data-ttu-id="55893-110">Proje</span><span class="sxs-lookup"><span data-stu-id="55893-110">Project</span></span> | <span data-ttu-id="55893-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55893-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="55893-112">İş parçacığı güvenli ve hiçbir zaman içeriklerini değiştirmek için kesin koleksiyonlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="55893-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="55893-113">Bir ileti işleyicisi sağlar <xref:System.Net.Http.HttpClient> Windows WinHTTP arabirimi esas alan.</span><span class="sxs-lookup"><span data-stu-id="55893-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="55893-114">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="55893-114">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="55893-115">SIMD donanım tabanlı hızlandırma yararlanabilirsiniz vektör türleri içeren bir kitaplık sağlar.</span><span class="sxs-lookup"><span data-stu-id="55893-115">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="55893-116">TPL veri akışı kitaplığı, eşzamanlılık kullanan uygulamaların sağlamlığını artırmak için veri akışı bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="55893-116">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="55893-117">Platforma özgü kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="55893-117">Platform-specific libraries</span></span>
  
| <span data-ttu-id="55893-118">Proje</span><span class="sxs-lookup"><span data-stu-id="55893-118">Project</span></span> | <span data-ttu-id="55893-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55893-119">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="55893-120">Genişletir <xref:System.Text.EncodingProvider> kod sayfası kodlamaları hedefleyen Evrensel Windows platformu uygulamaları için kullanılabilir hale getirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="55893-120">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="55893-121">Özel API'ler</span><span class="sxs-lookup"><span data-stu-id="55893-121">Private APIs</span></span>  

<span data-ttu-id="55893-122">Bu API, ürün altyapısını destekler ve amaçlayan/desteklenen doğrudan sizin kodunuzdan kullanılmak üzere değildir.</span><span class="sxs-lookup"><span data-stu-id="55893-122">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="55893-123">API adı</span><span class="sxs-lookup"><span data-stu-id="55893-123">API Name</span></span> |
| -------- |
| [<span data-ttu-id="55893-124">System.Net.Connection sınıfı</span><span class="sxs-lookup"><span data-stu-id="55893-124">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="55893-125">System.Net.Connection.m\_WriteList alan</span><span class="sxs-lookup"><span data-stu-id="55893-125">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="55893-126">System.Net.ConnectionGroup sınıfı</span><span class="sxs-lookup"><span data-stu-id="55893-126">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="55893-127">System.Net.ConnectionGroup.m\_ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="55893-127">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="55893-128">System.Net.CoreResponseData sınıfı</span><span class="sxs-lookup"><span data-stu-id="55893-128">System.Net.CoreResponseData Class</span></span>](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [<span data-ttu-id="55893-129">System.Net.CoreResponseData.m\_ResponseHeaders alan</span><span class="sxs-lookup"><span data-stu-id="55893-129">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="55893-130">System.Net.CoreResponseData.m\_StatusCode alan</span><span class="sxs-lookup"><span data-stu-id="55893-130">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="55893-131">System.Net.HttpWebRequest. \_AutoRedirects alan</span><span class="sxs-lookup"><span data-stu-id="55893-131">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="55893-132">System.Net.HttpWebRequest. \_CoreResponse alan</span><span class="sxs-lookup"><span data-stu-id="55893-132">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="55893-133">System.Net.HttpWebRequest. \_HttpResponse alan</span><span class="sxs-lookup"><span data-stu-id="55893-133">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="55893-134">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="55893-134">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="55893-135">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="55893-135">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="55893-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes alan</span><span class="sxs-lookup"><span data-stu-id="55893-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="55893-137">System.Windows.Forms.Design.DataMemberFieldEditor sınıfı</span><span class="sxs-lookup"><span data-stu-id="55893-137">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="55893-138">System.Windows.Forms.Design.DataMemberListEditor sınıfı</span><span class="sxs-lookup"><span data-stu-id="55893-138">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="55893-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55893-139">See also</span></span>

[<span data-ttu-id="55893-140">.NET Framework ve Bant Dışı Yayınlar</span><span class="sxs-lookup"><span data-stu-id="55893-140">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

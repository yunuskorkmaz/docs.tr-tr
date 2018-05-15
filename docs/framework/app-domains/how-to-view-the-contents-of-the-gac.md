---
title: 'Nasıl yapılır: Genel Derleme Önbelleğinin İçeriğini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e582f86eac03a51437b965f87f1bc7f29294eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="a8286-102">Nasıl yapılır: Genel Derleme Önbelleğinin İçeriğini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a8286-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="a8286-103">Kullanım [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) genel derleme önbelleğinin içeriğini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="a8286-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="a8286-104">Genel derleme önbelleğinde derleme listesi görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="a8286-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="a8286-105">Konumundaki [Visual Studio komut istemi](../../../docs/framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="a8286-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="a8286-106">**Gacutil -m** </span><span class="sxs-lookup"><span data-stu-id="a8286-106">**gacutil -l** </span></span>  
     <span data-ttu-id="a8286-107">-veya-</span><span class="sxs-lookup"><span data-stu-id="a8286-107">-or-</span></span>  
    <span data-ttu-id="a8286-108">**Gacutil /l**</span><span class="sxs-lookup"><span data-stu-id="a8286-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="a8286-109">.NET Framework'ün önceki sürümlerindeki [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows kabuk uzantısı, Genel Derleme Önbelleği dosya Gezgini'nde görüntülemek etkin.</span><span class="sxs-lookup"><span data-stu-id="a8286-109">In earlier versions of the .NET Framework, the [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="a8286-110">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a8286-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8286-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8286-111">See Also</span></span>  
 [<span data-ttu-id="a8286-112">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="a8286-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="a8286-113">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="a8286-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)

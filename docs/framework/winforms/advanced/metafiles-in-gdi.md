---
title: GDI+'da Meta Dosyaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: 73cacb7f701768b42121c31cfbc4f26905961231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525102"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="e748d-102">GDI+'da Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e748d-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e748d-103"> sağlar <xref:System.Drawing.Imaging.Metafile> kaydedin ve meta dosyaları görüntülemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e748d-103"> provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="e748d-104">Bir vektör görüntüsü olarak da adlandırılan meta dosyası komutları ve ayarlar çizim sırası depolanan resimdir.</span><span class="sxs-lookup"><span data-stu-id="e748d-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="e748d-105">Komutlar ve ayarlar kaydedilen bir <xref:System.Drawing.Imaging.Metafile> nesne bellekte veya bir dosya veya akışınıza kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="e748d-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="e748d-106">Meta dosyası biçimleri</span><span class="sxs-lookup"><span data-stu-id="e748d-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e748d-107"> Aşağıdaki biçimlerde depolanan meta dosyaları görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e748d-107"> can display metafiles that have been stored in the following formats:</span></span>  
  
-   <span data-ttu-id="e748d-108">Windows Meta dosyası (WMF)</span><span class="sxs-lookup"><span data-stu-id="e748d-108">Windows Metafile (WMF)</span></span>  
  
-   <span data-ttu-id="e748d-109">Geliştirilmiş Meta Dosyası (EMF)</span><span class="sxs-lookup"><span data-stu-id="e748d-109">Enhanced Metafile (EMF)</span></span>  
  
-   <span data-ttu-id="e748d-110">EMF +</span><span class="sxs-lookup"><span data-stu-id="e748d-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e748d-111"> meta dosyaları EMF ve EMF + biçimlerde ancak WMF biçiminde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e748d-111"> can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="e748d-112">EMF + uzantısıdır verir EMF için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] depolanması için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e748d-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="e748d-113">EMF + format iki çeşidi vardır: EMF + yalnızca ve EMF + çift.</span><span class="sxs-lookup"><span data-stu-id="e748d-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="e748d-114">EMF + yalnızca meta dosyaları içeren yalnızca [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e748d-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="e748d-115">Bu tür meta dosyaları tarafından görüntülenen [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ancak tarafından [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e748d-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="e748d-116">EMF + çift meta dosyaları içeren [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e748d-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="e748d-117">Her [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bir EMF + çift kaydında meta dosyası alternatif ile eşleştirilmiş [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] kaydı.</span><span class="sxs-lookup"><span data-stu-id="e748d-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="e748d-118">Bu tür meta dosyaları tarafından görüntülenen [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] veya [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e748d-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="e748d-119">Aşağıdaki örnek, bir dosya olarak daha önce kaydedilmiş bir meta dosyası görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e748d-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="e748d-120">Meta dosyası, sol üst köşesinde görüntülenir (100, 100).</span><span class="sxs-lookup"><span data-stu-id="e748d-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="e748d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e748d-121">See Also</span></span>  
 [<span data-ttu-id="e748d-122">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e748d-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)

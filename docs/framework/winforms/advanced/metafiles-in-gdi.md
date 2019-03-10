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
ms.openlocfilehash: 25ce3fdd98560aba0918431bb77d6f3f23a04784
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722470"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="1a1f6-102">GDI+'da Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="1a1f6-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="1a1f6-103">sağlar <xref:System.Drawing.Imaging.Metafile> kaydedebilir ve meta dosyaları görüntülemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-103">provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="1a1f6-104">Bir vektör görüntüsü olarak da adlandırılan bir meta dosyası, komutlar ve ayarlar çizim sırası depolanan bir görüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="1a1f6-105">Komutlar ve ayarlar kaydedilen bir <xref:System.Drawing.Imaging.Metafile> nesne bellekte veya bir dosya veya akışınıza kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="1a1f6-106">Meta dosyası biçimleri</span><span class="sxs-lookup"><span data-stu-id="1a1f6-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="1a1f6-107">Aşağıdaki biçimlerde depolanan meta görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a1f6-107">can display metafiles that have been stored in the following formats:</span></span>  
  
-   <span data-ttu-id="1a1f6-108">Windows Meta dosyası (WMF)</span><span class="sxs-lookup"><span data-stu-id="1a1f6-108">Windows Metafile (WMF)</span></span>  
  
-   <span data-ttu-id="1a1f6-109">Geliştirilmiş Meta Dosyası (EMF)</span><span class="sxs-lookup"><span data-stu-id="1a1f6-109">Enhanced Metafile (EMF)</span></span>  
  
-   <span data-ttu-id="1a1f6-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="1a1f6-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="1a1f6-111">meta dosyaları EMF ve EMF + biçimlerde ancak WMF biçiminde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-111">can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="1a1f6-112">EMF + veren EMF uzantısı olan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] depolanacak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="1a1f6-113">EMF + format iki çeşidi vardır: EMF + yalnızca ve EMF + çift.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="1a1f6-114">EMF + yalnızca meta dosyaları içeren yalnızca [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="1a1f6-115">Bu tür meta dosyaları tarafından görüntülenen [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ancak tarafından [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a1f6-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="1a1f6-116">EMF + çift meta dosyaları içeren [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="1a1f6-117">Her [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] EMF + çift kayıt meta dosyası bir alternatif ile eşleştirilmiş [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] kaydı.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="1a1f6-118">Bu tür meta dosyaları tarafından görüntülenen [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ya da [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a1f6-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="1a1f6-119">Aşağıdaki örnek, bir dosya olarak daha önce kaydedilmiş bir meta dosyası görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="1a1f6-120">Yazılmışsa, sol üst köşesinde görüntülenir (100, 100).</span><span class="sxs-lookup"><span data-stu-id="1a1f6-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="1a1f6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a1f6-121">See also</span></span>
- [<span data-ttu-id="1a1f6-122">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="1a1f6-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)

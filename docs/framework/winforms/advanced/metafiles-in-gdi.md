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
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504591"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="bf33a-102">GDI+'da Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="bf33a-102">Metafiles in GDI+</span></span>
<span data-ttu-id="bf33a-103">GDI + sağlar <xref:System.Drawing.Imaging.Metafile> kaydedebilir ve meta dosyaları görüntülemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="bf33a-103">GDI+ provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="bf33a-104">Bir vektör görüntüsü olarak da adlandırılan bir meta dosyası, komutlar ve ayarlar çizim sırası depolanan bir görüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="bf33a-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="bf33a-105">Komutlar ve ayarlar kaydedilen bir <xref:System.Drawing.Imaging.Metafile> nesne bellekte veya bir dosya veya akışınıza kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="bf33a-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="bf33a-106">Meta dosyası biçimleri</span><span class="sxs-lookup"><span data-stu-id="bf33a-106">Metafile Formats</span></span>  
 <span data-ttu-id="bf33a-107">GDI +'da aşağıdaki biçimlerde depolanan meta görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf33a-107">GDI+ can display metafiles that have been stored in the following formats:</span></span>  
  
- <span data-ttu-id="bf33a-108">Windows Meta dosyası (WMF)</span><span class="sxs-lookup"><span data-stu-id="bf33a-108">Windows Metafile (WMF)</span></span>  
  
- <span data-ttu-id="bf33a-109">Geliştirilmiş Meta Dosyası (EMF)</span><span class="sxs-lookup"><span data-stu-id="bf33a-109">Enhanced Metafile (EMF)</span></span>  
  
- <span data-ttu-id="bf33a-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="bf33a-110">EMF+</span></span>  
  
 <span data-ttu-id="bf33a-111">GDI +'da meta dosyaları EMF ve EMF + biçimlerde ancak WMF biçiminde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf33a-111">GDI+ can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="bf33a-112">EMF + depolanacak GDI +'da kayıtları veren EMF uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="bf33a-112">EMF+ is an extension to EMF that allows GDI+ records to be stored.</span></span> <span data-ttu-id="bf33a-113">EMF + format iki çeşidi vardır: EMF + yalnızca ve EMF + çift.</span><span class="sxs-lookup"><span data-stu-id="bf33a-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="bf33a-114">EMF + yalnızca meta dosyaları yalnızca GDI +'da kayıtları içerir.</span><span class="sxs-lookup"><span data-stu-id="bf33a-114">EMF+ Only metafiles contain only GDI+ records.</span></span> <span data-ttu-id="bf33a-115">Bu tür meta dosyaları tarafından GDI + ancak GDI görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf33a-115">Such metafiles can be displayed by GDI+ but not by GDI.</span></span> <span data-ttu-id="bf33a-116">GDI +'da ve GDI kayıtlarını EMF + çift meta dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="bf33a-116">EMF+ Dual metafiles contain GDI+ and GDI records.</span></span> <span data-ttu-id="bf33a-117">Bir çift EMF + meta dosyası her GDI +'da kayıt alternatif bir GDI kayıtla eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bf33a-117">Each GDI+ record in an EMF+ Dual metafile is paired with an alternate GDI record.</span></span> <span data-ttu-id="bf33a-118">Bu tür meta GDI veya GDI +'TARAFINDAN görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf33a-118">Such metafiles can be displayed by GDI+ or by GDI.</span></span>  
  
 <span data-ttu-id="bf33a-119">Aşağıdaki örnek, bir dosya olarak daha önce kaydedilmiş bir meta dosyası görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bf33a-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="bf33a-120">Yazılmışsa, sol üst köşesinde görüntülenir (100, 100).</span><span class="sxs-lookup"><span data-stu-id="bf33a-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="bf33a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf33a-121">See also</span></span>

- [<span data-ttu-id="bf33a-122">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="bf33a-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)

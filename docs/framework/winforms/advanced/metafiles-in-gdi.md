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
ms.openlocfilehash: bb972f158496192aa38f10564209bb2781837414
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119866"
---
# <a name="metafiles-in-gdi"></a>GDI+'da Meta Dosyaları
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sağlar <xref:System.Drawing.Imaging.Metafile> kaydedebilir ve meta dosyaları görüntülemek için sınıf. Bir vektör görüntüsü olarak da adlandırılan bir meta dosyası, komutlar ve ayarlar çizim sırası depolanan bir görüntüsüdür. Komutlar ve ayarlar kaydedilen bir <xref:System.Drawing.Imaging.Metafile> nesne bellekte veya bir dosya veya akışınıza kaydedildi.  
  
## <a name="metafile-formats"></a>Meta dosyası biçimleri  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Aşağıdaki biçimlerde depolanan meta görüntüleyebilirsiniz:  
  
-   Windows Meta dosyası (WMF)  
  
-   Geliştirilmiş Meta Dosyası (EMF)  
  
-   EMF+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] meta dosyaları EMF ve EMF + biçimlerde ancak WMF biçiminde kaydedebilirsiniz.  
  
 EMF + veren EMF uzantısı olan [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] depolanacak kaydeder. EMF + format iki çeşidi vardır: EMF + yalnızca ve EMF + çift. EMF + yalnızca meta dosyaları içeren yalnızca [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kaydeder. Bu tür meta dosyaları tarafından görüntülenen [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ancak tarafından [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]. EMF + çift meta dosyaları içeren [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] kaydeder. Her [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] EMF + çift kayıt meta dosyası bir alternatif ile eşleştirilmiş [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] kaydı. Bu tür meta dosyaları tarafından görüntülenen [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ya da [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 Aşağıdaki örnek, bir dosya olarak daha önce kaydedilmiş bir meta dosyası görüntüler. Yazılmışsa, sol üst köşesinde görüntülenir (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)

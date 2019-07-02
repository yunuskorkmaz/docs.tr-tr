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
# <a name="metafiles-in-gdi"></a>GDI+'da Meta Dosyaları
GDI + sağlar <xref:System.Drawing.Imaging.Metafile> kaydedebilir ve meta dosyaları görüntülemek için sınıf. Bir vektör görüntüsü olarak da adlandırılan bir meta dosyası, komutlar ve ayarlar çizim sırası depolanan bir görüntüsüdür. Komutlar ve ayarlar kaydedilen bir <xref:System.Drawing.Imaging.Metafile> nesne bellekte veya bir dosya veya akışınıza kaydedildi.  
  
## <a name="metafile-formats"></a>Meta dosyası biçimleri  
 GDI +'da aşağıdaki biçimlerde depolanan meta görüntüleyebilirsiniz:  
  
- Windows Meta dosyası (WMF)  
  
- Geliştirilmiş Meta Dosyası (EMF)  
  
- EMF+  
  
 GDI +'da meta dosyaları EMF ve EMF + biçimlerde ancak WMF biçiminde kaydedebilirsiniz.  
  
 EMF + depolanacak GDI +'da kayıtları veren EMF uzantısıdır. EMF + format iki çeşidi vardır: EMF + yalnızca ve EMF + çift. EMF + yalnızca meta dosyaları yalnızca GDI +'da kayıtları içerir. Bu tür meta dosyaları tarafından GDI + ancak GDI görüntülenebilir. GDI +'da ve GDI kayıtlarını EMF + çift meta dosyaları içerir. Bir çift EMF + meta dosyası her GDI +'da kayıt alternatif bir GDI kayıtla eşleştirilir. Bu tür meta GDI veya GDI +'TARAFINDAN görüntülenebilir.  
  
 Aşağıdaki örnek, bir dosya olarak daha önce kaydedilmiş bir meta dosyası görüntüler. Yazılmışsa, sol üst köşesinde görüntülenir (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)

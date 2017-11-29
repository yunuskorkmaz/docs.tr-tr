---
title: "GDI+'da Meta Dosyaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b75ceb08df0454172a000d5d1ad15445f685ddf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="metafiles-in-gdi"></a>GDI+'da Meta Dosyaları
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]sağlar <xref:System.Drawing.Imaging.Metafile> kaydedin ve meta dosyaları görüntülemek için sınıf. Bir vektör görüntüsü olarak da adlandırılan meta dosyası komutları ve ayarlar çizim sırası depolanan resimdir. Komutlar ve ayarlar kaydedilen bir <xref:System.Drawing.Imaging.Metafile> nesne bellekte veya bir dosya veya akışınıza kaydedildi.  
  
## <a name="metafile-formats"></a>Meta dosyası biçimleri  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Aşağıdaki biçimlerde depolanan meta dosyaları görüntüleyebilirsiniz:  
  
-   Windows Meta dosyası (WMF)  
  
-   Geliştirilmiş Meta Dosyası (EMF)  
  
-   EMF +  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]meta dosyaları EMF ve EMF + biçimlerde ancak WMF biçiminde kaydedebilirsiniz.  
  
 EMF + uzantısıdır verir EMF için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] depolanması için kaydeder. EMF + format iki çeşidi vardır: EMF + yalnızca ve EMF + çift. EMF + yalnızca meta dosyaları içeren yalnızca [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kaydeder. Bu tür meta dosyaları tarafından görüntülenen [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ancak tarafından [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]. EMF + çift meta dosyaları içeren [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] kaydeder. Her [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bir EMF + çift kaydında meta dosyası alternatif ile eşleştirilmiş [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] kaydı. Bu tür meta dosyaları tarafından görüntülenen [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] veya [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 Aşağıdaki örnek, bir dosya olarak daha önce kaydedilmiş bir meta dosyası görüntüler. Meta dosyası, sol üst köşesinde görüntülenir (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Resimler, bit eşlemler ve meta dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)

---
title: "GDI+'daki Bölgeler"
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
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0525e7b58353909d41e5367aa52a17aa56bcd77c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="regions-in-gdi"></a>GDI+'daki Bölgeler
Bir bölge, bir çıktı aygıtının görüntü alanını bölümüdür. Bölgeler (tek bir dikdörtgen) basit veya karmaşık (çokgenler ve kapalı Eğriler birleşimi) olabilir. İki bölgede aşağıda gösterilmiştir: bir bir dikdörtgen oluşturulur ve başka bir yoldan oluşturulur.  
  
 ![Bölgeler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>Bölgeleri Kullanma  
 Bölgeler kırpma için sık kullanılan ve isabet testi. Belirli bir bölgeye görüntü alanının genellikle güncelleştirilmesi gerekiyor bölümü çizim kısıtlama kırpma içerir. İsabet testi fare düğmesine basıldığında imleci ekranın belirli bir bölgede olup olmadığını belirlemek için denetimi içerir.  
  
 Dikdörtgene ya da bir yol bölgesinden oluşturabilirsiniz. Varolan bölgeleri birleştirerek karmaşık bölgeler de oluşturabilirsiniz. <xref:System.Drawing.Region> Sınıfı bölgeler birleştirmek için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, ve <xref:System.Drawing.Region.Complement%2A>.  
  
 İki bölgede kesişimi hem bölgelere ait olan tüm noktaları kümesidir. UNION bir ya da diğer veya her iki bölgeden ait tüm noktalarının kümesidir. Bir bölge tamamlama bölgede değil tüm noktaları kümesidir. Önceki çizimde gösterilen iki bölgede birleşimi ve kesişimi aşağıda gösterilmektedir.  
  
 ![Bölgeler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A> Bölgeler, çiftine uygulanan yöntem, tek bir bölge veya diğer, ancak ikisini ait tüm noktalarını içeren bir bölge üretir. <xref:System.Drawing.Region.Exclude%2A> Bölgeler, çiftine uygulanan yöntem, ilk bölgede ikinci bölgede değil tüm noktalarını içeren bir bölge üretir. Aşağıdaki çizimde uygulanmasından neden bölgeleri gösterir <xref:System.Drawing.Region.Xor%2A> ve <xref:System.Drawing.Region.Exclude%2A> yöntemleri için bu konunun başında gösterilen iki bölgede.  
  
 ![Bölgeler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 Bir bölge doldurmak için size gereken bir <xref:System.Drawing.Graphics> nesne, bir <xref:System.Drawing.Brush> nesnesi ve bir <xref:System.Drawing.Region> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.FillRegion%2A> yöntemi ve <xref:System.Drawing.Brush> nesnesi dolgu rengini veya desenini gibi özniteliklerini depolar. Aşağıdaki örnek, bir bölge düz renk ile doldurur.  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [Çizgiler, eğriler ve şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Bölgeleri kullanma](../../../../docs/framework/winforms/advanced/using-regions.md)

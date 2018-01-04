---
title: "Nasıl yapılır: Bir Bölgeyle Vuruş Sınaması Kullanma"
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
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c0766c989df7c2329aa4d36af834378b02b1301
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-hit-testing-with-a-region"></a>Nasıl yapılır: Bir Bölgeyle Vuruş Sınaması Kullanma
İsabet testi amacı, imleç üzerinden bir simge veya düğmesi gibi belirli bir nesne olup olmadığını belirlemektir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki dikdörtgen bölgeler birleşimi oluşturan tarafından artı şeklinde bir bölge oluşturur. Varsayımında değişkeni `point` en son tıklatın konumunu tutar. Kod bakar olup olmadığını `point` içinde artı şeklinde bölgedir. Noktanın bölge (isabet) ise, bölge donuk kırmızı fırça ile doldurulur. Aksi takdirde, bölge yarı saydam kırmızı fırça ile doldurulur.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Region>  
 [GDI+'daki Bölgeler](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)

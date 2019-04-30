---
title: 'Nasıl yapılır: Bir Bölgeyle Vuruş Sınaması Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 136f15f1364fb2aed791b4a61d0f11411b055967
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778878"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>Nasıl yapılır: Bir Bölgeyle Vuruş Sınaması Kullanma
İsabet sınaması amacı, imleci üzerine bir simge veya düğmesi gibi belirli bir nesne olup olmadığını belirlemektir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki dikdörtgen bölge birleşimi oluşturan tarafından artı şeklindeki bir bölge oluşturur. Varsayımında değişkeni `point` en son tıklayarak konumunu içerir. Kod bakar olmadığını `point` artı şeklindeki bölgede. (İsabet) bölgede noktasıysa bölge donuk bir kırmızı fırça ile doldurulur. Aksi takdirde, bölge, yarı saydam fırçalarla kırmızı fırça ile doldurulur.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Region>
- [GDI+'daki Bölgeler](regions-in-gdi.md)
- [Nasıl yapılır: Bir bölgeyle kırpma kullanma](how-to-use-clipping-with-a-region.md)

---
title: Gerçek Koordinat Dönüştürmesini Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: f40d7e8cb814344365e8b88c2659751903b79d77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969149"
---
# <a name="using-the-world-transformation"></a>Gerçek Koordinat Dönüştürmesini Kullanma
Gerçek koordinat dönüştürmesini parçasıdır <xref:System.Drawing.Graphics> sınıfı. Gerçek koordinat dönüştürmesini belirtin sayıları depolanan bir <xref:System.Drawing.Drawing2D.Matrix> 3 × 3 matrisi temsil eden nesne. <xref:System.Drawing.Drawing2D.Matrix> Ve <xref:System.Drawing.Graphics> sınıflarının sayıları dünya dönüşümü matriste ayarlamak için çeşitli yöntemler vardır.  
  
## <a name="different-types-of-transformations"></a>Farklı tür dönüşümleri  
 Aşağıdaki örnekte, kod ilk 50 x 50 Dikdörtgen oluşturur ve kaynak (0, 0) bulur. Kaynak istemci alanını sol üst köşesinde ' dir.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 Aşağıdaki kod, dikdörtgen x yönünde 1.75 faktörüyle genişleyen veya 0,5 y yönünde faktörüyle dikdörtgen bir ölçekleme dönüşümü geçerlidir:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 X yönünde uzun ve kısa y yönünde özgün bir dikdörtgen sonucudur.  
  
 Ölçeklendirme yerine dikdörtgen döndürmek için aşağıdaki kodu kullanın:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 Dikdörtgen çevirmek için aşağıdaki kodu kullanın:  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Drawing2D.Matrix>
- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
- [Yönetilen GDI+'da Dönüştürmeleri Kullanma](using-transformations-in-managed-gdi.md)

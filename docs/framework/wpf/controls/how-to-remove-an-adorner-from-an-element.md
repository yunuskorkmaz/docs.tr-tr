---
title: 'Nasıl yapılır: Öğeden Donatıcıyı Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: 0c74fe9ed1e7190ce4ff26a7dbae1413f950ba7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374082"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>Nasıl yapılır: Öğeden Donatıcıyı Kaldırma
Bu örnek program aracılığıyla belirli bir donatıcı belirtilen bir kaldırma işlemi gösterilmektedir <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Örnek  
 Bu ayrıntılı kod örneğinde ilk donatıcı donatıcıları tarafından döndürülen dizi kaldırır <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  Donatıcıları almak için bu örnek olur bir <xref:System.Windows.UIElement> adlı *myTextBox*.  Öğe çağrısında belirtilmişse <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> hiçbir donatıcıları sahip `null` döndürülür.  Bu kod açıkça boş bir dize arar ve burada null dizide nispeten daha sık karşılaşılan olması beklenir uygulamaları için idealdir.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>Örnek  
 Bu sıkıştırılmış kod örneği, yukarıda gösterilen ayrıntılı bir örnek için işlevsel olarak eşdeğerdir. Mümkün olduğu için bu kodu boş bir dize açıkça denetlemez, bir <xref:System.NullReferenceException> özel durum yükseltilebilir.  Bu kod burada null dizide nadir olması beklenir uygulamaları için idealdir.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Donatıcılara Genel Bakış](adorners-overview.md)

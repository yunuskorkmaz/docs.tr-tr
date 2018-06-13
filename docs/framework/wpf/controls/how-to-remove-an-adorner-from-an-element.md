---
title: 'Nasıl yapılır: Öğeden Donatıcıyı Kaldırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: a3e1b08a9ec5e2cd60c063ced5e5f0d5874f8184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551849"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>Nasıl yapılır: Öğeden Donatıcıyı Kaldırma
Bu örnek program aracılığıyla belirli donatıcının belirtilen bir nasıl kaldırılacağını gösterir <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Örnek  
 Bu ayrıntılı kod örneği tarafından döndürülen donatıcı dizisinden ilk donatıcıyı kaldırır <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  Donatıcılar almak için bu örnek olur bir <xref:System.Windows.UIElement> adlı *myTextBox*.  Öğe çağrısında belirtilmişse <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> hiçbir Donatıcılar sahip `null` döndürülür.  Bu kod açıkça boş bir dize arar ve boş bir dizi görece yaygın olarak beklenirken uygulamalar için uygundur.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>Örnek  
 Bu sıkıştırılmış kod örneği, yukarıda gösterilen ayrıntılı örneğe işlevsel olarak eşdeğerdir. Mümkün olması için bu kodu boş dize, açıkça denetlemez, bir <xref:System.NullReferenceException> özel durum oluşturuldu.  Bu kod boş bir dizi seyrek olarak beklenirken uygulamalar için uygundur.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Donatıcılara Genel Bakış](../../../../docs/framework/wpf/controls/adorners-overview.md)

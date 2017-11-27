---
title: "Nasıl yapılır: Öğeden Tüm Donatıcıları Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9b69b9150e8d2c2938c53fcd47e72b7fcb6d238
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-remove-all-adorners-from-an-element"></a>Nasıl yapılır: Öğeden Tüm Donatıcıları Kaldırma
Bu örnek program aracılığıyla tüm donatıcıların belirtilen bir nasıl kaldırılacağını gösterir <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Örnek  
 Bu ayrıntılı kod örneği tüm tarafından döndürülen donatıcı dizisinden kaldırır <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  Donatıcılar almak için bu örnek olur bir <xref:System.Windows.UIElement> adlı *myTextBox*.  Öğe çağrısında belirtilmişse <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> hiçbir Donatıcılar sahip `null` döndürülür.  Bu kod açıkça boş bir dize arar ve boş bir dizi görece yaygın olarak beklenirken uygulamalar için uygundur.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a>Örnek  
 Bu sıkıştırılmış kod örneği, yukarıda gösterilen ayrıntılı örneğe işlevsel olarak eşdeğerdir. Mümkün olması için bu kodu boş dize, açıkça denetlemez, bir <xref:System.NullReferenceException> özel durum oluşturuldu.  Bu kod boş bir dizi seyrek olarak beklenirken uygulamalar için uygundur.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Donatıcılar genel bakış](../../../../docs/framework/wpf/controls/adorners-overview.md)

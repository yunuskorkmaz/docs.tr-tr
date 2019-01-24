---
title: 'Nasıl yapılır: Donatıcı Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: f34bdeb87d0bf34a998f9b2e2fb6c42aedec5063
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591688"
---
# <a name="how-to-implement-an-adorner"></a>Nasıl yapılır: Donatıcı Uygulama
Bu örnekte, en az donatıcı uygulama gösterilmektedir.  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Donatıcıları herhangi devralınan işleme davranışını içermez dikkat edin önemlidir; öğeye bir donatıcı oluşturulduğunu sağlama donatıcı uygulayan sorumluluğundadır.   Geçersiz kılmak için işleme davranışını uygulamanın yaygın bir yolu olan <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> (Bu örnekte gösterildiği gibi) gerektiği gibi donatıcının görseller oluşturmak için nesne.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Özet devralan bir sınıf uygulama tarafından oluşturulan özel bir donatıcı <xref:System.Windows.Documents.Adorner> sınıfı.  Örnek donatıcı köşelerini yalnızca daireler donatır bir <xref:System.Windows.UIElement> kılarak daireler ile <xref:System.Windows.UIElement.OnRender%2A> yöntemi.  
  
### <a name="code"></a>Kod  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Donatıcılara Genel Bakış](../../../../docs/framework/wpf/controls/adorners-overview.md)

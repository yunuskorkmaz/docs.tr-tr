---
title: "Nasıl yapılır: Donatıcı Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76bceae5b69fad4c217127617309484edcf18108
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-adorner"></a>Nasıl yapılır: Donatıcı Uygulama
Bu örnek, en az donatıcı uygulamasını gösterir.  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Donatıcılar herhangi devralınmış işleme davranışını içermez dikkate almak önemlidir; donatıcı işler sağlama donatıcı uygulayan sorumluluğundadır.   İşleme davranışını uygulamanın en yaygın yolu geçersiz kılmaktır <xref:System.Windows.UIElement.OnRender%2A> yöntemi ve bir veya daha fazla <xref:System.Windows.Media.DrawingContext> donatıcının (Bu örnekte gösterildiği gibi) gereken görsellerini işlemek için nesneleri.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Özel bir donatıcı Özet devralan bir sınıf uygulama tarafından oluşturulan <xref:System.Windows.Documents.Adorner> sınıfı.  Örnek donatıcı yalnızca köşelerinde daireler donatır bir <xref:System.Windows.UIElement> kılarak daireler ile <xref:System.Windows.UIElement.OnRender%2A> yöntemi.  
  
### <a name="code"></a>Kod  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Donatıcılara Genel Bakış](../../../../docs/framework/wpf/controls/adorners-overview.md)

---
title: "Nasıl yapılır: Bir Öğe veya Fırça Opaklığına Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 808d29292e176af8d3af1fc0f4a02c48ee05ea35
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Nasıl yapılır: Bir Öğe veya Fırça Opaklığına Animasyon Ekleme
Görünüm ve bu moddan silinerek çerçeve öğesi yapmak için animasyon uygulayabilirsiniz kendi <xref:System.Windows.UIElement.Opacity%2A> özellik veya animasyon <xref:System.Windows.Media.Brush.Opacity%2A> özelliği <xref:System.Windows.Media.Brush> (veya Fırçalar) onu boyamak için kullanılan. Kolaylaştırır öğenin opaklık animasyon ve alt görünümü ve bu moddan silinerek, ancak öğe boyamak için kullanılan fırça animasyon öğesi hangi kısmının belirerek hakkında daha fazla seçmeli olarak sağlar. Örneğin, bir düğmenin arka planını boyamak için kullanılan fırça geçirgenliğini animasyon. Bu, içeri ve dışarı görünümünün metnini tamamıyla opak bırakarak sırasında silinerek için düğmenin arka plan neden olur.  
  
> [!NOTE]
>  Animasyon <xref:System.Windows.Media.Brush.Opacity%2A> , bir <xref:System.Windows.Media.Brush> animasyon üzerinden performans avantajı sağlar <xref:System.Windows.UIElement.Opacity%2A> bir öğenin özelliği.  
  
 Böylece Görünüm ve bu moddan silinerek aşağıdaki örnekte, iki düğme oynatılır. İlk geçirgenliğini <xref:System.Windows.Controls.Button> gelen animasyonlu `1.0` için `0.0` üzerinden bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniye. İkinci düğme ayrıca animasyonlu ancak SolidColorBrush kısmını boyamak için kullanılan kendi <xref:System.Windows.Controls.Control.Background%2A> tüm düğmenin geçirgenliğini yerine animasyonlu. Örnek çalıştırdığınızda, yalnızca ikinci düğmenin arka plan Görünüm ve bu moddan belirerek sırada ilk düğme tamamen görünümü ve bu moddan kaybolur. Metni ve kenarlığı tamamen donuk kalır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 Kod bu örnekten çıkarılmıştır. Tam örnek ayrıca geçirgenliğini animasyon gösterilmektedir bir <xref:System.Windows.Media.Color> içinde bir <xref:System.Windows.Media.LinearGradientBrush>.  Tam bir örnek için bkz: [öğesi örneği geçirgenliğini animasyon](http://go.microsoft.com/fwlink/?LinkID=159968).

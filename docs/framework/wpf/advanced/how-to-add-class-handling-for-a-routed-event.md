---
title: 'Nasıl yapılır: Yönlendirilmiş Olay için Sınıf İşleme Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 7b897954cbdab461dc0305c6290e67c1af5282c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777045"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>Nasıl yapılır: Yönlendirilmiş Olay için Sınıf İşleme Ekleme
Yönlendirilmiş olaylar, sınıf veya örnek işleyicileri verilen herhangi bir düğümde rotadaki tarafından işlenebilir. Sınıf işleyicileri önce çağrılır ve olayların örnek işlemesini gizlemenize veya temel sınıflar tarafından sahip olunan olayları Olay belirli davranışları tanıtmak için sınıf uygulamaları tarafından kullanılabilir. Bu örnekte, sınıf işleyicileri uygulamak için yakından ilgili iki teknik gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte göre özel bir sınıf <xref:System.Windows.Controls.Canvas> paneli. Uygulamanın temel şirket içi özel bir sınıf davranışlarını herhangi bir sol fare düğmesine tıkladığında kesintiye ve alt öğe sınıfı veya herhangi bir örnek işleyicileri çağrılacak önce bunları işlenmiş olarak işaretleme dahil olmak üzere, kendi alt öğeleri içermesidir.  
  
 <xref:System.Windows.UIElement> Sınıfı sağlar sınıfını işleme sanal bir yöntemi gösterir <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> olay yalnızca kılarak olayı. Bu sınıf işleme yere sınıfı hiyerarşisinde sanal bir yöntem varsa uygulamak için en basit yoludur. Aşağıdaki kodda gösterildiği <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> "türetilir MyEditContainer" uygulamasında <xref:System.Windows.Controls.Canvas>. Uygulama olay bağımsız değişkenlerde işlenmiş olarak işaretler ve ardından kaynak öğesi temel görünür bir değişiklik vermek için kod ekler.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Sanal temel sınıflar veya o belirli yöntemi varsa, sınıf işleme yardımcı yöntemi kullanarak doğrudan eklenebilir <xref:System.Windows.EventManager> sınıfı <xref:System.Windows.EventManager.RegisterClassHandler%2A>. Bu yöntem, yalnızca sınıf işleme ekleme sınıfların statik başlatma çağrılmalıdır. Bu örnek için başka bir işleyici ekler <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , ve bu durumda kayıtlı sınıf özel bir sınıftır. Buna karşılık, sanalları kullanırken, kayıtlı gerçekten sınıftır <xref:System.Windows.UIElement> temel sınıfı. Burada temel sınıflar ve alt sınıf işleme kaydetme durumlarda, alt sınıf işleyicileri önce çağrılır. Bir uygulamanın davranışı Bu işleyici, bir ileti kutusu ilk gösterebilir ve ardından sanal yöntemin işleyicisi visual değişiklik gösterilen olacaktır.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.EventManager>
- [Yönlendirilmiş Olayları İşlenmiş Olarak İşaretleme ve Sınıf İşlemesi](marking-routed-events-as-handled-and-class-handling.md)
- [Yönlendirilmiş Olayı İşleme](how-to-handle-a-routed-event.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)

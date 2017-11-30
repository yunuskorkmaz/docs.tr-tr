---
title: "Nasıl yapılır: Gönderilmiş bir Olay için Sınıf İşleme Ekleme"
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
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abbbdce0ca12c4d8bdd12f616bf49c3d6f66f441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>Nasıl yapılır: Gönderilmiş bir Olay için Sınıf İşleme Ekleme
Yönlendirilmiş olaylar, sınıf veya örnek işleyicileri verilen herhangi bir düğümde rotadaki tarafından işlenebilir. Sınıf işleyicileri önce çağrılır ve olayların örnek işlemesini bastırmak veya diğer olaya özgü davranışlar temel sınıflar tarafından sahip olunan olaylarına tanıtmak için sınıf uygulamaları tarafından kullanılabilir. Bu örnek sınıf işleyicileri uygulamak için iki yakından ilgili teknik gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnek dayalı özel bir sınıf kullanır <xref:System.Windows.Controls.Canvas> paneli. Uygulama özel bir sınıf herhangi bir sol fare düğmesini tıklattığında kesintiye uğratan ve alt öğe sınıfı veya herhangi bir örnek işleyicileri çağrılacak önce bunları ele işaretleme dahil olmak üzere, kendi alt öğeleri üzerinde davranışlar tanıtır dayanır.  
  
 <xref:System.Windows.UIElement> Sınıfı sınıf üzerinde işlemesini sağlayan sanal bir yöntem sunar <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> olay yalnızca kılarak olay. Sanal bir yöntem herhangi bir yerde, sınıf hiyerarşisinde kullanılabilir durumdaysa sınıf işleme uygulamak için en basit yolu budur. Aşağıdaki kodda gösterildiği <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> "türetildiği MyEditContainer" uygulamasında <xref:System.Windows.Controls.Canvas>. Uygulama olay değişkenlerinde işlenmiş olarak işaretler ve temel görünür bir değişikliğe source öğesi vermek için bazı kod ekler.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Sanal Taban sınıflar veya bu belirli yöntem için kullanılabilir ise, sınıf işleme yardımcı yöntemi kullanarak doğrudan eklenebilir <xref:System.Windows.EventManager> sınıfı, <xref:System.Windows.EventManager.RegisterClassHandler%2A>. Bu yöntem yalnızca statik sınıf işleme ekleme sınıfları başlatma içinde çağrılmalıdır. Bu örnek için başka bir işleyici ekler <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , ve bu durumda kayıtlı sınıf özel bir sınıftır. Buna karşılık, sanalların, kayıtlı sınıf gerçekten kullanıldığında <xref:System.Windows.UIElement> temel sınıfı. Burada temel sınıflar ve alt sınıfların her sınıf işleme kaydettiği durumlarda alt sınıf işleyicileri önce çağrılır. Bir uygulamanın davranışı, bu işleyici, ileti kutusu ilk gösterir ve daha sonra sanal yöntemin işleyicisi görsel değişiklikleri gösterilen olacaktır.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.EventManager>  
 [İşaretleme yönlendirilmiş olarak işlenen ve sınıf işlemesi olaylar](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Yönlendirilmiş olay işleme](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [Yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)

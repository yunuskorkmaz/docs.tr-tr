---
title: "Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme"
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
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c923a24f5abfdb059a436206a15181a67d03068f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme
Bu konuda nasıl kullanılacağını açıklar <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> zamanlamasını bağlama kaynak güncelleştirmeleri denetlemek için özellik. Konu kullanır <xref:System.Windows.Controls.TextBox> denetim bir örnek olarak.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Özelliğine sahip bir varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Bu bir uygulama olup olmadığını anlamına gelir. bir <xref:System.Windows.Controls.TextBox> veri bağlama ile <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> özelliği, yazdığınız içine metin <xref:System.Windows.Controls.TextBox> kadar kaynak güncelleştirmez <xref:System.Windows.Controls.TextBox> odağı kaybettiğinde (örneğin, tıkladığınızda çıktığınızda <xref:System.Windows.Controls.TextBox>).  
  
 Kaynak olarak güncelleştirilmesini istiyorsanız yazıyorsanız, Ayarla <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlamanın <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Aşağıdaki örnekte, `Text` her ikisi de özelliklerini <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBlock> aynı kaynak özelliğe bağlıdır. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Özelliği <xref:System.Windows.Controls.TextBox> bağlama ayarlanmış <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 Sonuç olarak, <xref:System.Windows.Controls.TextBlock> (kaynak değiştiğinden) metne kullanıcının girdiği aynı metni gösterir <xref:System.Windows.Controls.TextBox>örnek aşağıdaki ekran görüntüsü tarafından gösterildiği gibi:  
  
 ![Basit veri bağlama örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Bir iletişim kutusu veya kullanıcı tarafından düzenlenebilir bir forma sahip ve kullanıcı alanları düzenleme tamamlandı ve "Tamam" seçeneğine tıklar kadar kaynak güncelleştirmelerinin erteleneceği istediğiniz, ayarlayabileceğiniz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlamaları için değerini <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, aşağıdaki örnekte olduğu gibi:  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Ayarladığınızda <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değeri <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, uygulama çağırdığında kaynak değeri yalnızca değiştirir <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> yöntemi. Aşağıdaki örnekte nasıl çağrılacağını gösterir <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> için `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Diğer denetimlerin özellikleri için aynı yöntemleri kullanabilirsiniz, ancak diğer özelliklerin çoğu varsayılan olduğunu aklınızda bulundurun <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Daha fazla bilgi için bkz: <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özellik sayfası.  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Özelliği kaynak güncelleştirmeleri ile ilgilenir ve bu nedenle yalnızca ilgili <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlar. İçin <xref:System.Windows.Data.BindingMode.TwoWay> ve <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalarının çalışması için özellik değişikliği bildirimlerini sağlaması kaynak nesnesi gerekiyor. Daha fazla bilgi için bu konudaki bildirdi örnekleri başvurabilirsiniz. Ayrıca, bakabilirsiniz [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

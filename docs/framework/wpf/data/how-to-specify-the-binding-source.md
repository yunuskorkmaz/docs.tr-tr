---
title: "Nasıl yapılır: Bağlama Kaynağı Belirtme"
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
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05f77e8939b9b81a9e3861df6a44bc3585a0a504
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-binding-source"></a>Nasıl yapılır: Bağlama Kaynağı Belirtme
Veri bağlama bağlama kaynak nesnesi verilerinizden elde ettiğiniz nesneye başvurur. Bu konuda bağlama kaynağını belirterek, farklı yolları açıklanmaktadır.  
  
## <a name="example"></a>Örnek  
 Ortak bir kaynağa çeşitli özellikler bağlıyorsanız, kullanmak istediğiniz `DataContext` tüm veri bağlama özellikleri devralındığı ortak bir kaynaktan kapsamı oluşturmak için kullanışlı bir yol sağlayan özelliği.  
  
 Aşağıdaki örnekte, veri bağlamı uygulama kök öğe üzerinde oluşturulur. Bu, veri bağlamı devralmak tüm alt öğeleri sağlar. Veri bağlama için gelen bir özel veri sınıftan `NetIncome`, doğrudan bir eşleme aracılığıyla başvurulan ve kaynak anahtarı verilen `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 Aşağıdaki örnek tanımını gösterir `NetIncome` sınıfı.  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  Yukarıdaki örnek biçimlendirme nesnesinde oluşturur ve bir kaynak olarak kullanır. Kodda bir zaten örneği bir nesneyi bağlamak istiyorsanız, ayarlamanız gerekir `DataContext` özelliği programlı olarak. Bir örnek için bkz: [veri kullanılabilir yap XAML'de bağlama için](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).  
  
 Alternatif olarak, kaynak belirtmek istiyorsanız, tek tek bağlantılarına açıkça aşağıdaki seçenekleriniz vardır. Bunlar devralınan veri bağlamı üzerinde önceliklidir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Bir nesnenin örneğine kaynak ayarlamak için bu özelliği kullanın. Bir kapsamda oluşturma işlevselliğini gerekmiyorsa çeşitli özelliklerin aynı veri bağlamından devralınan, kullanabileceğiniz <xref:System.Windows.Data.Binding.Source%2A> özelliği yerine `DataContext` özelliği. Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Bağlamanın hedef olduğu göre kaynak belirtmek istediğinizde kullanışlıdır. Bu özellik burada kullanabilir bazı yaygın senaryolar, öğesinin bir özelliğini aynı öğenin başka bir özelliği Bağla istediğinizde veya bir bağlama stil veya şablonunda tanımlıyorsanız olur. Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Bağlamak istediğiniz öğeyi temsil eden bir dize belirtin. Bu, uygulamanızın üzerinde başka bir öğenin özelliği bağlamak istediğiniz durumunda faydalı olur. Kullanmak istiyorsanız, örneğin, bir <xref:System.Windows.Controls.Slider> , uygulamanızda başka bir denetimin yüksekliğini denetlemek için veya bağlamak istiyorsanız <xref:System.Windows.Controls.ContentControl.Content%2A> için denetiminizin <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliği, <xref:System.Windows.Controls.ListBox> denetim. Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>  
 [Özellik değeri devralma](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)  
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Bağlama bildirimleri genel bakış](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

---
title: 'Nasıl yapılır: Bağlama Kaynağı Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 105924fec2956f2f74a2a574ee62f71a37df9366
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356727"
---
# <a name="how-to-specify-the-binding-source"></a>Nasıl yapılır: Bağlama Kaynağı Belirtme
Veri bağlamasında bağlama kaynak nesnesi verilerinizden elde ettiğiniz nesneye başvurur. Bu konu, bağlama kaynağı belirtme farklı yollarını açıklar.  
  
## <a name="example"></a>Örnek  
 Çeşitli özellikler için ortak bir kaynaktan bağlanıyorsanız, kullanmak istediğiniz `DataContext` tüm veri bağlı özelliklerinin içinde ortak bir kaynaktan devralındığı bir kapsamı'kurmak için kullanışlı bir yol sağlayan bir özellik.  
  
 Aşağıdaki örnekte, uygulamanın kök öğe üzerinde veri bağlamı kuruldu. Bu, söz konusu veri bağlamı devralan tüm alt öğeleri sağlar. Veri bağlama için gelen bir özel veri sınıftan `NetIncome`, doğrudan bir eşlemesi aracılığıyla başvurulan ve kaynak anahtarı verilen `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 Aşağıdaki örnek tanımı gösterilmektedir `NetIncome` sınıfı.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  Yukarıdaki örnek biçimlendirmede nesnesini başlatır ve bir kaynak olarak kullanır. Ayarlamak gereken kodu zaten oluşturulmuş bir nesneyi bağlamak istiyorsanız, `DataContext` özelliğini program aracılığıyla. Bir örnek için bkz. [olun veri kullanılabilir için XAML bağlamasında](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Alternatif olarak, kaynak belirtmek istiyorsanız, ayrı ayrı oturumdaki bağlamalarda açıkça aşağıdaki seçenekleriniz vardır. Bunlar devralınan veri bağlamından önceliklidir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Bir nesnenin örneğine kaynağı ayarlamak için bu özelliği kullanın. Bir kapsamda oluşturma işlevselliğini gerekmiyorsa çeşitli özelliklerin aynı veri bağlamını devralır, kullanabileceğiniz <xref:System.Windows.Data.Binding.Source%2A> özelliği yerine `DataContext` özelliği. Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Bu, bağlama hedefi olduğu göre kaynak belirtmek istediğinizde kullanışlıdır. Burada, bu özelliği kullanabilirsiniz bazı yaygın senaryolar öğenizin bir özellik aynı öğenin başka bir özelliğine bağlamak istediğinizde veya bir bağlama bir stil veya şablonun içinde tanımlıyorsanız olur. Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Bağlamak istediğiniz öğeyi temsil eden bir dize belirtin. Uygulamanızdaki başka bir öğenin özelliğe bağlamak istediğinizde bu kullanışlıdır. Örneğin kullanmak istiyorsanız, bir <xref:System.Windows.Controls.Slider> uygulamanızın başka bir denetimin yüksekliği denetlemek için veya bağlamak istiyorsanız <xref:System.Windows.Controls.ContentControl.Content%2A> denetiminizin için <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliği, <xref:System.Windows.Controls.ListBox> denetimi. Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Özellik Değeri Devralma](../advanced/property-value-inheritance.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Bağlama Bildirimlerine Genel Bakış](binding-declarations-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)

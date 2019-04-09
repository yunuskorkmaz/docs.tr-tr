---
title: 'Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 5272a19f69b3caf80fd7d5187c9a6a386cd44621
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143279"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme
Bu konu nasıl kullanılacağını açıklar <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> zamanlamasını bağlama kaynağı güncelleştirmeleri denetlemek için özellik. Konu kullanır <xref:System.Windows.Controls.TextBox> örnek olarak denetimi.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> özelliğine sahip bir varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Bu bir uygulama olup olmadığını anlamına gelir. bir <xref:System.Windows.Controls.TextBox> verilere bağlı ile <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> özelliği, denetimine yazdığınız metnin <xref:System.Windows.Controls.TextBox> kadar kaynak güncelleştirmez <xref:System.Windows.Controls.TextBox> odağı kaybettiğinde (örneğin tıkladığınızda liste kutusundan <xref:System.Windows.Controls.TextBox>).  
  
 Siz yazarken güncelleştirilecek kaynak istiyorsanız ayarlayın <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlamanın <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Kod vurgulanan satırları aşağıdaki örnekte, gösteren `Text` özelliklerinin her ikisi de <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBlock> aynı kaynak özelliğine bağlıdır. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Özelliği <xref:System.Windows.Controls.TextBox> bağlama ayarlandığında <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 Sonuç olarak, <xref:System.Windows.Controls.TextBlock> (kaynak değiştiğinden dolayı) kullanıcının girdiği metin olarak aynı metni gösterir <xref:System.Windows.Controls.TextBox>tarafından örnek aşağıdaki ekran görüntüsünde gösterildiği gibi:  
  
 ![Basit veri bağlama örnek ekran](./media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Bir iletişim kutusu veya kullanıcı tarafından düzenlenebilir bir forma sahip ve kullanıcı alanları düzenleme bitti ve "Tamam" a tıklayarak kadar kaynak güncelleştirmelerinin erteleneceği istediğiniz, ayarlayabileceğiniz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlamalarınızı için değerini <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, aşağıdaki örnekte olduğu gibi:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Ayarladığınızda <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, uygulama çağırdığında kaynak değeri yalnızca değişiklikleri <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> yöntemi. Aşağıdaki örnek nasıl çağrılacağını gösterir <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> için `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Diğer denetimlerin özelliklerini açma için aynı tekniği, ancak diğer özelliklerin çoğu varsayılan olduğunu aklınızda bulundurun <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Daha fazla bilgi için <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özellik sayfası.  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Özelliği kaynak güncelleştirmeleriyle ilgilenir ve bu nedenle yalnızca ilgili <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlar. İçin <xref:System.Windows.Data.BindingMode.TwoWay> ve <xref:System.Windows.Data.BindingMode.OneWayToSource> çalışmak için özellik değişikliği bildirimleri sağlamak için kaynak nesnesi gereksinimlerini bağlamalar. Daha fazla bilgi için bu konuda bahsedilen örnekleri başvurabilirsiniz. Ayrıca, bakabilirsiniz [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)

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
ms.openlocfilehash: d1d624d7550a1135431b7fffc7450e3a510855a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966465"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme
Bu konuda, <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlama kaynak güncelleştirmelerinin zamanlamasını denetlemek için özelliğinin nasıl kullanılacağı açıklanmaktadır. Konuda bir örnek olarak <xref:System.Windows.Controls.TextBox> denetim kullanılmaktadır.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> özelliğin varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>değeri vardır. Bu, bir uygulamanın veri ile bağlantılı <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox>olan bir uygulamasına sahip olması anlamına gelir.<xref:System.Windows.Controls.TextBox.Text%2A> özelliği, içine <xref:System.Windows.Controls.TextBox> yazdığınız metin, odağı <xref:System.Windows.Controls.TextBox> kaybetene kadar kaynağı güncelleştirmez (örneğin, öğesinden <xref:System.Windows.Controls.TextBox>uzağa tıkladığınızda).  
  
 Kaynağı yazarken güncelleştirilmesini istiyorsanız, bağlamasının öğesini olarak <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>ayarlayın. Aşağıdaki örnekte, vurgulanmış kod satırları, `Text` <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBlock> öğelerinin özelliklerinin aynı kaynak özelliğine bağlandığını gösterir. Bağlamanın özelliği olarak<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>ayarlanır. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Controls.TextBox>  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 Sonuç <xref:System.Windows.Controls.TextBlock> olarak, örneğin aşağıdaki ekran görüntüsünde gösterildiği gibi, Kullanıcı <xref:System.Windows.Controls.TextBox>içine metin girerken aynı metni (kaynak değiştiği için) gösterir:  
  
 ![Basit veri bağlamayı gösteren ekran görüntüsü.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)  
  
 Bir iletişim kutusu veya Kullanıcı tarafından düzenlenebilir bir formunuz varsa ve Kullanıcı alanları düzenleyip "Tamam" düğmesini tıklayana kadar kaynak güncelleştirmelerini erteleyebilirsiniz, aşağıdaki örnekte olduğu gibi <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>Bağlamalarınızın değerini olarak ayarlayabilirsiniz:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Değerini <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> olarak <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>ayarladığınızda kaynak değeri yalnızca uygulama yöntemi çağırdığında değişir. Aşağıdaki örnek, için <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> `itemNameTextBox`nasıl çağrılacağını göstermektedir:  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
> Diğer denetimlerin özellikleri için aynı tekniği kullanabilirsiniz, ancak diğer özelliklerin çoğu için varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bir <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>değere sahip olduğunu aklınızda bulundurun. Daha fazla bilgi için, bkz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> . Özellik sayfası.  
  
> [!NOTE]
> Özelliği, kaynak güncelleştirmeleriyle ilgilidir ve bu nedenle yalnızca <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalarla ilgilidir. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.BindingMode.TwoWay> Ve<xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaların çalışması için kaynak nesnenin özellik değişikliği bildirimleri sağlaması gerekir. Daha fazla bilgi için, bu konuda alıntı yapılan örneklere başvurabilirsiniz. Ayrıca, [özellik değiştirme bildirimini Uygula](how-to-implement-property-change-notification.md)' ya bakabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)

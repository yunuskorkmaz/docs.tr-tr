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
ms.openlocfilehash: b211eb67e3bac95f74255935a39cc0d6aec61531
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974780"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme
Bu konuda, bağlama kaynak güncelleştirmelerinin zamanlamasını denetlemek için <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliğinin nasıl kullanılacağı açıklanmaktadır. Konu, örnek olarak <xref:System.Windows.Controls.TextBox> denetimini kullanır.

## <a name="example"></a>Örnek
 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> özelliği, <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerine sahiptir. Bu, bir uygulamanın veri bağlantılı <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> özelliği olan bir <xref:System.Windows.Controls.TextBox> varsa, <xref:System.Windows.Controls.TextBox> yazdığınız metin <xref:System.Windows.Controls.TextBox> odağı kaybetene kadar kaynağı güncelleştirmez (örneğin, <xref:System.Windows.Controls.TextBox>uzağa tıkladığınızda).

 Kaynağı yazarken güncelleştirilmesini isterseniz, bağlamanın <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>olarak ayarlayın. Aşağıdaki örnekte, vurgulanmış kod satırları <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBlock> `Text` özelliklerinin aynı kaynak özelliğine bağlandığını gösterir. <xref:System.Windows.Controls.TextBox> bağlamasının <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>olarak ayarlanmıştır.

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 Sonuç olarak, <xref:System.Windows.Controls.TextBlock>, kullanıcının aşağıdaki ekran görüntüsünde gösterildiği gibi, <xref:System.Windows.Controls.TextBox>metin girerken aynı metni (kaynak değiştiği için) gösterir:

 ![Basit veri bağlamayı gösteren ekran görüntüsü.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Bir iletişim kutusu veya Kullanıcı tarafından düzenlenebilir formunuz varsa ve Kullanıcı alanları düzenleyip "Tamam" düğmesini tıklayana kadar kaynak güncelleştirmelerini ertemek istiyorsanız, Bağlamalarınızın <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini aşağıdaki örnekte olduğu gibi <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>olarak ayarlayabilirsiniz:

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>olarak ayarladığınızda, kaynak değeri yalnızca uygulama <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> yöntemini çağırdığında değişir. Aşağıdaki örnek, `itemNameTextBox`için <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> nasıl çağrılacağını gösterir:

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Diğer denetimlerin özellikleri için aynı tekniği kullanabilirsiniz, ancak diğer özelliklerin çoğu <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerine sahip olduğunu aklınızda bulundurun. Daha fazla bilgi için <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Özellik sayfasına bakın.

> [!NOTE]
> <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği, kaynak güncelleştirmeleriyle ilgilidir ve bu nedenle yalnızca <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaları için geçerlidir. <xref:System.Windows.Data.BindingMode.TwoWay> ve <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalarının çalışması için, kaynak nesnenin özellik değişikliği bildirimleri sağlaması gerekir. Daha fazla bilgi için, bu konuda alıntı yapılan örneklere başvurabilirsiniz. Ayrıca, [özellik değiştirme bildirimini Uygula](how-to-implement-property-change-notification.md)' ya bakabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)

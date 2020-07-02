---
title: 'Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme'
description: Windows Presentation Foundation (WPF) içindeki UpdateSourceTrigger özelliğini kullanarak bağlama kaynak güncelleştirmelerinin zamanlamasını denetleyin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 8f6eb5beb0d14a951f6e6cf6eb81e130f5a3e194
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622789"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme
Bu konuda, <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlama kaynak güncelleştirmelerinin zamanlamasını denetlemek için özelliğinin nasıl kullanılacağı açıklanmaktadır. Konuda <xref:System.Windows.Controls.TextBox> bir örnek olarak denetim kullanılmaktadır.

## <a name="example"></a>Örnek
 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>Özelliğin varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değeri vardır <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> . Bu, bir uygulamanın <xref:System.Windows.Controls.TextBox> veri bağlantılı özelliği olan bir özelliğine sahip olması durumunda <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> , içine yazdığınız metin <xref:System.Windows.Controls.TextBox> odağı kaybetene kadar kaynağı güncelleştirmez <xref:System.Windows.Controls.TextBox> (örneğin, ' den uzağa tıkladığınızda <xref:System.Windows.Controls.TextBox> ).

 Kaynağı yazarken güncelleştirilmesini istiyorsanız, <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlamasının öğesini olarak ayarlayın <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> . Aşağıdaki örnekte, vurgulanmış kod satırları `Text` , ve öğelerinin özelliklerinin <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBlock> aynı kaynak özelliğine bağlandığını gösterir. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Controls.TextBox> Bağlamanın özelliği olarak ayarlanır <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> .

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 Sonuç olarak, örneğin <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox> aşağıdaki ekran görüntüsünde gösterildiği gibi, Kullanıcı içine metin girerken aynı metni (kaynak değiştiği için) gösterir:

 ![Basit veri bağlamayı gösteren ekran görüntüsü.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Bir iletişim kutusu veya Kullanıcı tarafından düzenlenebilir bir formunuz varsa ve Kullanıcı alanları düzenleyip "Tamam" düğmesini tıklayana kadar kaynak güncelleştirmelerini erteleyebilirsiniz, <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> Aşağıdaki örnekte olduğu gibi Bağlamalarınızın değerini olarak ayarlayabilirsiniz:

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Değerini olarak ayarladığınızda <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> kaynak değeri yalnızca uygulama yöntemi çağırdığında değişir <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> . Aşağıdaki örnek, için nasıl çağrılacağını <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> göstermektedir `itemNameTextBox` :

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Diğer denetimlerin özellikleri için aynı tekniği kullanabilirsiniz, ancak diğer özelliklerin çoğu için varsayılan bir değere sahip olduğunu aklınızda bulundurun <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> . Daha fazla bilgi için, bkz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> . Özellik sayfası.

> [!NOTE]
> <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Özelliği, kaynak güncelleştirmeleriyle ilgilidir ve bu nedenle yalnızca <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalarla ilgilidir. <xref:System.Windows.Data.BindingMode.TwoWay>Ve <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaların çalışması için kaynak nesnenin özellik değişikliği bildirimleri sağlaması gerekir. Daha fazla bilgi için, bu konuda alıntı yapılan örneklere başvurabilirsiniz. Ayrıca, [özellik değiştirme bildirimini Uygula](how-to-implement-property-change-notification.md)' ya bakabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)

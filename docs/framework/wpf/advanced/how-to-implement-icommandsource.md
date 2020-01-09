---
title: 'Nasıl yapılır: ICommandSource Uygulama'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 755377d25a2deb48aa9da86d4182075e30763530
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345092"
---
# <a name="how-to-implement-icommandsource"></a>Nasıl yapılır: ICommandSource Uygulama

Bu örnek, <xref:System.Windows.Input.ICommandSource>uygulayarak bir komut kaynağının nasıl oluşturulacağını gösterir. Komut kaynağı bir komutun nasıl çağıralınacağını bilen bir nesnedir. <xref:System.Windows.Input.ICommandSource> arabirimi üç üye kullanıma sunar:

- <xref:System.Windows.Input.ICommandSource.Command%2A>: çağrılacak komut.
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: komut kaynağından komutu işleyen yönteme geçirilen kullanıcı tanımlı bir veri türü.
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: komutun yürütüldüğü nesne.

Bu örnekte, <xref:System.Windows.Controls.Slider> denetiminden devralan ve <xref:System.Windows.Input.ICommandSource> arabirimini uygulayan bir sınıf oluşturulur.
  
## <a name="example"></a>Örnek

WPF, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>ve <xref:System.Windows.Documents.Hyperlink>gibi <xref:System.Windows.Input.ICommandSource>uygulayan bir dizi sınıf sağlar. Komut kaynağı bir komutu nasıl çağırdığını tanımlar. Bu sınıflar tıklandıklarında bir komutu çağırır ve yalnızca <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği ayarlandığında bir komut kaynağı haline gelir.

Bu örnekte, <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği değiştirildiğinde, kaydırıcı taşındığında veya daha doğru bir şekilde, komutunu çağıracaksınız.

Sınıf tanımı aşağıda verilmiştir:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

Sonraki adım <xref:System.Windows.Input.ICommandSource> üyelerini uygulamaktır. Bu örnekte, Özellikler <xref:System.Windows.DependencyProperty> nesne olarak uygulanır. Bu, özelliklerin veri bağlamayı kullanmasına olanak sağlar. <xref:System.Windows.DependencyProperty> sınıfı hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md). Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

Burada yalnızca <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği gösterilmiştir.
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<xref:System.Windows.DependencyProperty> değiştirme geri çağırması aşağıda verilmiştir:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

Sonraki adım, komut kaynağıyla ilişkili komutu eklemek ve kaldırmak. Yeni bir komut eklendiğinde <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği yalnızca üzerine yazılamaz, çünkü önceki komutla ilişkili olay işleyicileri, varsa, önce kaldırılmalıdır.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

Sonraki adım <xref:System.Windows.Input.ICommand.CanExecuteChanged> işleyicisi için mantık oluşturmaktır.

<xref:System.Windows.Input.ICommand.CanExecuteChanged> olay, komut kaynağını, komutun geçerli komut hedefinde yürütme yeteneğinin değişmiş olabileceğini bildirir. Bir komut kaynağı bu olayı aldığında, genellikle komutta <xref:System.Windows.Input.ICommand.CanExecute%2A> yöntemini çağırır. Komut geçerli komut hedefinde yürütülemediğinde, komut kaynağı genellikle kendisini devre dışı bırakır. Komut geçerli komut hedefinde yürütülebiliyorsanız, komut kaynağı genellikle kendisini etkinleştirir.

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

Son adım <xref:System.Windows.Input.ICommand.Execute%2A> yöntemidir. Komut bir <xref:System.Windows.Input.RoutedCommand>ise, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntemi çağrılır; Aksi takdirde, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> yöntemi çağrılır.

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Komut Vermeye Genel Bakış](commanding-overview.md)

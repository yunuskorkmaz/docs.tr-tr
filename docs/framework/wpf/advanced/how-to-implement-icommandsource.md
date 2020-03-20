---
title: 'Nasıl yapılır: ICommandSource Uygulama'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6c18e0b77ec53d9bd3e7ce610f2940effe603c88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174699"
---
# <a name="how-to-implement-icommandsource"></a>Nasıl yapılır: ICommandSource Uygulama

Bu örnek, uygulayarak <xref:System.Windows.Input.ICommandSource>nasıl bir komut kaynağı oluşturmak için gösterir. Komut kaynağı, komut çağırmayı bilen bir nesnedir. Arabirim <xref:System.Windows.Input.ICommandSource> üç üyeyi ortaya çıkarır:

- <xref:System.Windows.Input.ICommandSource.Command%2A>: çağrılacak komut.
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: komut kaynağından komutu işleyen yönteme geçirilen kullanıcı tanımlı bir veri türü.
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: komutun yürütüldettiği nesne.

Bu örnekte, <xref:System.Windows.Controls.Slider> denetimden devralan ve <xref:System.Windows.Input.ICommandSource> arabirimi uygulayan bir sınıf oluşturulur.
  
## <a name="example"></a>Örnek

<xref:System.Windows.Input.ICommandSource>WPF, <xref:System.Windows.Controls.Button>, , <xref:System.Windows.Controls.MenuItem>ve <xref:System.Windows.Documents.Hyperlink>. Bir komut kaynağı komutu nasıl çağırdığını tanımlar. Bu sınıflar tıklatıldığında bir komut çağırır ve yalnızca malları <xref:System.Windows.Input.ICommandSource.Command%2A> ayarlandığında bir komut kaynağı haline gelir.

Bu örnekte, kaydırıcı taşındığında veya daha doğru suyla, özellik <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> değiştirildiğinde komutu çağırırsınız.

Sınıf tanımı aşağıdadır:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

Bir sonraki adım <xref:System.Windows.Input.ICommandSource> üyeleri uygulamaktır. Bu örnekte, özellikler nesne <xref:System.Windows.DependencyProperty> olarak uygulanır. Bu, özelliklerin veri bağlama yı kullanmasını sağlar. <xref:System.Windows.DependencyProperty> Sınıf hakkında daha fazla bilgi için Bağımlılık Özellikleri Genel [Bakış'a](dependency-properties-overview.md)bakın. Veri bağlama hakkında daha fazla bilgi için [Veri Bağlama Genel Bakışı'na](../../../desktop-wpf/data/data-binding-overview.md)bakın.

Burada <xref:System.Windows.Input.ICommandSource.Command%2A> yalnızca özellik gösterilir.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
Değişiklik geri <xref:System.Windows.DependencyProperty> arama aşağıdaki gibidir:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

Bir sonraki adım, komut kaynağıyla ilişkili komutu eklemek ve kaldırmaktır. Yeni <xref:System.Windows.Input.ICommandSource.Command%2A> bir komut eklendiğinde özellik yalnızca üzerine yazılamaz, çünkü önceki komutla ilişkili olay işleyicileri, varsa, önce kaldırılması gerekir.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

Bir sonraki adım <xref:System.Windows.Input.ICommand.CanExecuteChanged> işleyici için mantık oluşturmaktır.

Olay, <xref:System.Windows.Input.ICommand.CanExecuteChanged> komut kaynağına, komutun geçerli komut hedefinde yürütme yeteneğinin değişmiş olabileceğini belirtir. Bir komut kaynağı bu olayı aldığında, <xref:System.Windows.Input.ICommand.CanExecute%2A> genellikle komut üzerindeki yöntemi çağırır. Komut geçerli komut hedefinde yürütülemiyorsa, komut kaynağı genellikle kendisini devre dışı bolur. Komut geçerli komut hedefiüzerinde yürütebilir, komut kaynağı genellikle kendini etkinleştirmek olacaktır.

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

Son adım <xref:System.Windows.Input.ICommand.Execute%2A> yöntemdir. Komut a <xref:System.Windows.Input.RoutedCommand>ise, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntem denir; aksi takdirde, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> yöntem denir.

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Komut Vermeye Genel Bakış](commanding-overview.md)

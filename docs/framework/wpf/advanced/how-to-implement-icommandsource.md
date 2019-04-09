---
title: 'Nasıl yapılır: ICommandSource Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 218a17f221598ac29213bd28a0f04adb16bc933b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107373"
---
# <a name="how-to-implement-icommandsource"></a>Nasıl yapılır: ICommandSource Uygulama
Bu örnek, bir komut kaynak uygulayarak oluşturma işlemi gösterilmektedir <xref:System.Windows.Input.ICommandSource>.  Komut kaynak komutu çağırmak bildiği bir nesnedir.  <xref:System.Windows.Input.ICommandSource> Arabirimi kullanıma sunan üç üye: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, ve <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> Çağrılacak komut olur. <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> Komut kaynağından komutunu yürüten yönteme geçirilen kullanıcı tanımlı veri türü. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Komutu üzerinde yürütülmekte olan nesnesidir.  
  
 Bu örnekte, bir sınıf alt oluşturulur <xref:System.Windows.Controls.Slider> denetimi ve uygular <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulayan sınıflar sunar <xref:System.Windows.Input.ICommandSource>, gibi <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, ve <xref:System.Windows.Controls.ListBoxItem>.  Komut kaynak nasıl çalıştırılacağını tanımlar.   <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.MenuItem> tıklandığında bir komutunu çağırın.  A <xref:System.Windows.Controls.ListBoxItem> çift tıklandığında bir komut çalıştırır. Bu sınıflar yalnızca bir komut haline kaynağı kendi <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği ayarlanmış.  
  
 Bu örnekte, kaydırıcıyı taşındığında komutu çağırılır ya da daha doğru bir şekilde zaman <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği.  
  
 Sınıf tanımı aşağıda verilmiştir.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 Sonraki adım uygulamaktır <xref:System.Windows.Input.ICommandSource> üyeleri.  Bu örnekte, özellikleri olarak uygulanır <xref:System.Windows.DependencyProperty> nesneleri.  Bu, veri bağlama kullanılacak özellikleri sağlar.  Hakkında daha fazla bilgi için <xref:System.Windows.DependencyProperty> sınıfı [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).  Veri bağlama hakkında daha fazla bilgi için bkz. [Data Binding Overview](../data/data-binding-overview.md).  
  
 Yalnızca <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği burada gösterilmiştir.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Aşağıdaki <xref:System.Windows.DependencyProperty> geri çağırma değiştirin.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 Sonraki adım, ekleme ve kaldırma komut kaynağı ile ilişkili olan komutunu sağlamaktır.  <xref:System.Windows.Input.ICommandSource.Command%2A> Özelliği yalnızca yazılamıyor yeni bir komut eklendiğinde olay işleyicileri önceki komutla ilişkili olduğundan varsa, kaldırılmalıdır.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 Son adım için mantığı oluşturmaktır <xref:System.Windows.Input.ICommand.CanExecuteChanged> işleyicisi ve <xref:System.Windows.Input.ICommand.Execute%2A> yöntemi.  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged> Olay, komutun geçerli komut hedefi üzerinde yürütme yeteneği değişmiş olan komut kaynak bildirir.  Komut kaynak bu olayı aldığında, genellikle çağrıları <xref:System.Windows.Input.ICommand.CanExecute%2A> yöntemi komutu.  Geçerli komut hedefi üzerinde komut yürütülemezse, komut kaynak genellikle kendisini devre dışı bırakır.  Komutun geçerli komut hedefi üzerinde yürütebilir, komut kaynak genellikle kendisini etkinleştirir.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 Son adım <xref:System.Windows.Input.ICommand.Execute%2A> yöntemi.  Komut ise bir <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntemdir; tersi durumda, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> yöntemi çağrılır.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Komut Vermeye Genel Bakış](commanding-overview.md)

---
title: 'Nasıl yapılır: ICommandSource Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 9308bfbbb7fff86ca5e93c1155cc29e4ee0d05f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-icommandsource"></a>Nasıl yapılır: ICommandSource Uygulama
Bu örnek uygulama tarafından bir komut kaynağı oluşturmak nasıl gösterir <xref:System.Windows.Input.ICommandSource>.  Komutu bir komut çağrılacak bildiği bir nesne kaynağıdır.  <xref:System.Windows.Input.ICommandSource> Bir arabirimi kullanıma sunan üç üye: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, ve <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> çağrılacak komuttur. <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> Komut kaynağından komutu işleyen yönteme geçirilen bir kullanıcı tanımlı veri türü. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Komut üzerinde yürütülmekte olan nesnesidir.  
  
 Bu örnekte, bir sınıf alt oluşturulur <xref:System.Windows.Controls.Slider> denetimi ve uygulayan <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] arabirimini uygulayan sınıflar sayısını sağlar <xref:System.Windows.Input.ICommandSource>, gibi <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, ve <xref:System.Windows.Controls.ListBoxItem>.  Komut kaynak nasıl çalıştırılacağını tanımlar.   <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.MenuItem> bunlar tıklatıldığında bir komut çağırılır.  A <xref:System.Windows.Controls.ListBoxItem> çift tıklatıldığında bir komutu çalıştırır. Bu sınıfların yalnızca bir komut haline kaynağı kendi <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği ayarlanmış.  
  
 Kaydırıcı taşındığında komutu çağırılır bu örneğin ya da daha doğru bir şekilde zaman <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği değiştirildi.  
  
 Sınıf tanımı aşağıda verilmiştir.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 Sonraki adım uygulamaktır <xref:System.Windows.Input.ICommandSource> üyeleri.  Bu örnekte, özellikleri olarak uygulanan <xref:System.Windows.DependencyProperty> nesneleri.  Bu veri bağlama kullanmak üzere özelliklerini sağlar.  Hakkında daha fazla bilgi için <xref:System.Windows.DependencyProperty> sınıfı için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Yalnızca <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği burada gösterilir.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Aşağıdaki <xref:System.Windows.DependencyProperty> geri çağırma değiştirin.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 Sonraki adım, komut kaynağı ile ilişkili olan komut ekleyip olmaktır.  <xref:System.Windows.Input.ICommandSource.Command%2A> Özelliği yalnızca yazılamıyor yeni bir komut eklendiğinde, olay işleyicileri önceki komutla ilişkili olduğundan varsa, kaldırılmalıdır.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 Son adım için mantığı oluşturmaktır <xref:System.Windows.Input.ICommand.CanExecuteChanged> işleyici ve <xref:System.Windows.Input.ICommand.Execute%2A> yöntemi.  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged> Olay geçerli komut hedefinde yürütülecek komut yeteneklerini değişmiş olabilir komut kaynağı bildirir.  Komut kaynak bu olayı aldığında, genellikle çağırır <xref:System.Windows.Input.ICommand.CanExecute%2A> yöntemi komutu.  Komut geçerli komut hedefinde yürütülemezse, komut kaynağı genellikle kendisini devre dışı bırakır.  Komut geçerli komut hedefinde yürütüyorsa komut kaynağı genellikle kendisini etkinleştirir.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 Son adım <xref:System.Windows.Input.ICommand.Execute%2A> yöntemi.  Komut ise bir <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntemdir; tersi durumda, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> yöntemi çağrılır.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Input.ICommandSource>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.Input.RoutedCommand>  
 [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)

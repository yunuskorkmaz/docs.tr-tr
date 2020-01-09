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
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="1207e-102">Nasıl yapılır: ICommandSource Uygulama</span><span class="sxs-lookup"><span data-stu-id="1207e-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="1207e-103">Bu örnek, <xref:System.Windows.Input.ICommandSource>uygulayarak bir komut kaynağının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1207e-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="1207e-104">Komut kaynağı bir komutun nasıl çağıralınacağını bilen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1207e-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="1207e-105"><xref:System.Windows.Input.ICommandSource> arabirimi üç üye kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="1207e-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="1207e-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: çağrılacak komut.</span><span class="sxs-lookup"><span data-stu-id="1207e-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="1207e-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: komut kaynağından komutu işleyen yönteme geçirilen kullanıcı tanımlı bir veri türü.</span><span class="sxs-lookup"><span data-stu-id="1207e-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="1207e-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: komutun yürütüldüğü nesne.</span><span class="sxs-lookup"><span data-stu-id="1207e-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="1207e-109">Bu örnekte, <xref:System.Windows.Controls.Slider> denetiminden devralan ve <xref:System.Windows.Input.ICommandSource> arabirimini uygulayan bir sınıf oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1207e-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="1207e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1207e-110">Example</span></span>

<span data-ttu-id="1207e-111">WPF, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>ve <xref:System.Windows.Documents.Hyperlink>gibi <xref:System.Windows.Input.ICommandSource>uygulayan bir dizi sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="1207e-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="1207e-112">Komut kaynağı bir komutu nasıl çağırdığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1207e-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="1207e-113">Bu sınıflar tıklandıklarında bir komutu çağırır ve yalnızca <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği ayarlandığında bir komut kaynağı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1207e-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="1207e-114">Bu örnekte, <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği değiştirildiğinde, kaydırıcı taşındığında veya daha doğru bir şekilde, komutunu çağıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="1207e-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="1207e-115">Sınıf tanımı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1207e-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="1207e-116">Sonraki adım <xref:System.Windows.Input.ICommandSource> üyelerini uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="1207e-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="1207e-117">Bu örnekte, Özellikler <xref:System.Windows.DependencyProperty> nesne olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1207e-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="1207e-118">Bu, özelliklerin veri bağlamayı kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1207e-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="1207e-119"><xref:System.Windows.DependencyProperty> sınıfı hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1207e-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="1207e-120">Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1207e-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="1207e-121">Burada yalnızca <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1207e-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="1207e-122"><xref:System.Windows.DependencyProperty> değiştirme geri çağırması aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1207e-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="1207e-123">Sonraki adım, komut kaynağıyla ilişkili komutu eklemek ve kaldırmak.</span><span class="sxs-lookup"><span data-stu-id="1207e-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="1207e-124">Yeni bir komut eklendiğinde <xref:System.Windows.Input.ICommandSource.Command%2A> özelliği yalnızca üzerine yazılamaz, çünkü önceki komutla ilişkili olay işleyicileri, varsa, önce kaldırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1207e-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="1207e-125">Sonraki adım <xref:System.Windows.Input.ICommand.CanExecuteChanged> işleyicisi için mantık oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="1207e-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="1207e-126"><xref:System.Windows.Input.ICommand.CanExecuteChanged> olay, komut kaynağını, komutun geçerli komut hedefinde yürütme yeteneğinin değişmiş olabileceğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="1207e-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="1207e-127">Bir komut kaynağı bu olayı aldığında, genellikle komutta <xref:System.Windows.Input.ICommand.CanExecute%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="1207e-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="1207e-128">Komut geçerli komut hedefinde yürütülemediğinde, komut kaynağı genellikle kendisini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1207e-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="1207e-129">Komut geçerli komut hedefinde yürütülebiliyorsanız, komut kaynağı genellikle kendisini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1207e-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="1207e-130">Son adım <xref:System.Windows.Input.ICommand.Execute%2A> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="1207e-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="1207e-131">Komut bir <xref:System.Windows.Input.RoutedCommand>ise, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntemi çağrılır; Aksi takdirde, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1207e-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="1207e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1207e-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="1207e-133">Komut Vermeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1207e-133">Commanding Overview</span></span>](commanding-overview.md)

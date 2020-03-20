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
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="9eaf0-102">Nasıl yapılır: ICommandSource Uygulama</span><span class="sxs-lookup"><span data-stu-id="9eaf0-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="9eaf0-103">Bu örnek, uygulayarak <xref:System.Windows.Input.ICommandSource>nasıl bir komut kaynağı oluşturmak için gösterir.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="9eaf0-104">Komut kaynağı, komut çağırmayı bilen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="9eaf0-105">Arabirim <xref:System.Windows.Input.ICommandSource> üç üyeyi ortaya çıkarır:</span><span class="sxs-lookup"><span data-stu-id="9eaf0-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="9eaf0-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: çağrılacak komut.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="9eaf0-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: komut kaynağından komutu işleyen yönteme geçirilen kullanıcı tanımlı bir veri türü.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="9eaf0-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: komutun yürütüldettiği nesne.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="9eaf0-109">Bu örnekte, <xref:System.Windows.Controls.Slider> denetimden devralan ve <xref:System.Windows.Input.ICommandSource> arabirimi uygulayan bir sınıf oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="9eaf0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9eaf0-110">Example</span></span>

<span data-ttu-id="9eaf0-111"><xref:System.Windows.Input.ICommandSource>WPF, <xref:System.Windows.Controls.Button>, , <xref:System.Windows.Controls.MenuItem>ve <xref:System.Windows.Documents.Hyperlink>.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="9eaf0-112">Bir komut kaynağı komutu nasıl çağırdığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="9eaf0-113">Bu sınıflar tıklatıldığında bir komut çağırır ve yalnızca malları <xref:System.Windows.Input.ICommandSource.Command%2A> ayarlandığında bir komut kaynağı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="9eaf0-114">Bu örnekte, kaydırıcı taşındığında veya daha doğru suyla, özellik <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> değiştirildiğinde komutu çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="9eaf0-115">Sınıf tanımı aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="9eaf0-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="9eaf0-116">Bir sonraki adım <xref:System.Windows.Input.ICommandSource> üyeleri uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="9eaf0-117">Bu örnekte, özellikler nesne <xref:System.Windows.DependencyProperty> olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="9eaf0-118">Bu, özelliklerin veri bağlama yı kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="9eaf0-119"><xref:System.Windows.DependencyProperty> Sınıf hakkında daha fazla bilgi için Bağımlılık Özellikleri Genel [Bakış'a](dependency-properties-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="9eaf0-120">Veri bağlama hakkında daha fazla bilgi için [Veri Bağlama Genel Bakışı'na](../../../desktop-wpf/data/data-binding-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="9eaf0-121">Burada <xref:System.Windows.Input.ICommandSource.Command%2A> yalnızca özellik gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="9eaf0-122">Değişiklik geri <xref:System.Windows.DependencyProperty> arama aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9eaf0-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="9eaf0-123">Bir sonraki adım, komut kaynağıyla ilişkili komutu eklemek ve kaldırmaktır.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="9eaf0-124">Yeni <xref:System.Windows.Input.ICommandSource.Command%2A> bir komut eklendiğinde özellik yalnızca üzerine yazılamaz, çünkü önceki komutla ilişkili olay işleyicileri, varsa, önce kaldırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="9eaf0-125">Bir sonraki adım <xref:System.Windows.Input.ICommand.CanExecuteChanged> işleyici için mantık oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="9eaf0-126">Olay, <xref:System.Windows.Input.ICommand.CanExecuteChanged> komut kaynağına, komutun geçerli komut hedefinde yürütme yeteneğinin değişmiş olabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="9eaf0-127">Bir komut kaynağı bu olayı aldığında, <xref:System.Windows.Input.ICommand.CanExecute%2A> genellikle komut üzerindeki yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="9eaf0-128">Komut geçerli komut hedefinde yürütülemiyorsa, komut kaynağı genellikle kendisini devre dışı bolur.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="9eaf0-129">Komut geçerli komut hedefiüzerinde yürütebilir, komut kaynağı genellikle kendini etkinleştirmek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="9eaf0-130">Son adım <xref:System.Windows.Input.ICommand.Execute%2A> yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="9eaf0-131">Komut a <xref:System.Windows.Input.RoutedCommand>ise, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntem denir; aksi takdirde, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> yöntem denir.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="9eaf0-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9eaf0-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="9eaf0-133">Komut Vermeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9eaf0-133">Commanding Overview</span></span>](commanding-overview.md)

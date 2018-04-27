---
title: 'Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ff6cf75a18f9a19cc6649f551d5630d4d69dde8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="082fb-102">Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="082fb-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="082fb-103"><xref:System.Windows.Forms.BindingSource> Bileşen otomatik olarak saptar değişiklikleri bir veri kaynağı türü, veri kaynağı uygular, bağımsız <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve başlatır <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> bir özellik değeri değiştiğinde olaylar.</span><span class="sxs-lookup"><span data-stu-id="082fb-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="082fb-104">Denetimlerin bağlı olduğundan bu işlem faydalı olur <xref:System.Windows.Forms.BindingSource> sonra veri kaynağı değerleri değiştikçe otomatik olarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="082fb-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="082fb-105">Implements, veri kaynağı, <xref:System.ComponentModel.INotifyPropertyChanged> ve zaman uyumsuz işlemleri gerçekleştiren, arka plan iş parçacığında veri kaynağına değişiklik yapmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="082fb-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="082fb-106">Bunun yerine, arka plan iş parçacığında verileri okumak ve kullanıcı Arabirimi iş parçacığı listede verileri birleştirin.</span><span class="sxs-lookup"><span data-stu-id="082fb-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="082fb-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="082fb-107">Example</span></span>  
 <span data-ttu-id="082fb-108">Aşağıdaki kod örneğinde basit bir uygulama ortaya koyar <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="082fb-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="082fb-109">Ayrıca gösterir nasıl <xref:System.Windows.Forms.BindingSource> otomatik olarak, bir veri kaynağı değişikliği geçirir denetlemek için bir sınır <xref:System.Windows.Forms.BindingSource> listesine bağlı <xref:System.ComponentModel.INotifyPropertyChanged> türü.</span><span class="sxs-lookup"><span data-stu-id="082fb-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="082fb-110">Kullanırsanız `CallerMemberName` özniteliği, çağrıları `NotifyPropertyChanged` yöntemi dize bağımsız değişkeni özellik adını belirtmek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="082fb-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="082fb-111">Daha fazla bilgi için bkz: [arayan bilgileri](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span><span class="sxs-lookup"><span data-stu-id="082fb-111">For more information, see [Caller Information](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="082fb-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="082fb-112">Compiling the Code</span></span>  
 <span data-ttu-id="082fb-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="082fb-113">This example requires:</span></span>  
  
-   <span data-ttu-id="082fb-114">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="082fb-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="082fb-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="082fb-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="082fb-116">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="082fb-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="082fb-117">Ayrıca bkz. [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="082fb-117">Also see [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082fb-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="082fb-118">See Also</span></span>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [<span data-ttu-id="082fb-119">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="082fb-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="082fb-120">Nasıl yapılır: BindingSource ve ResetItem Metodunu Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="082fb-120">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)

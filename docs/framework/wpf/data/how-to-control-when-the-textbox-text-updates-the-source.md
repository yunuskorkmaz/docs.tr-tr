---
title: "Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00fc64938e6a063ffbda77961f967e08c169ebd7
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="87252-102">Nasıl yapılır: TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme</span><span class="sxs-lookup"><span data-stu-id="87252-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="87252-103">Bu konuda nasıl kullanılacağını açıklar <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> zamanlamasını bağlama kaynak güncelleştirmeleri denetlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="87252-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="87252-104">Konu kullanır <xref:System.Windows.Controls.TextBox> denetim bir örnek olarak.</span><span class="sxs-lookup"><span data-stu-id="87252-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87252-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="87252-105">Example</span></span>  
 <span data-ttu-id="87252-106"><xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Özelliğine sahip bir varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="87252-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="87252-107">Bu bir uygulama olup olmadığını anlamına gelir. bir <xref:System.Windows.Controls.TextBox> veri bağlama ile <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> özelliği, yazdığınız içine metin <xref:System.Windows.Controls.TextBox> kadar kaynak güncelleştirmez <xref:System.Windows.Controls.TextBox> odağı kaybettiğinde (örneğin, tıkladığınızda çıktığınızda <xref:System.Windows.Controls.TextBox>).</span><span class="sxs-lookup"><span data-stu-id="87252-107">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="87252-108">Siz yazarken güncelleştirilmesi kaynak istiyorsanız ayarlayın <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlamanın <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="87252-108">If you want the source to be updated as you type, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="87252-109">Aşağıdaki örnekte, kod vurgulanan satırlar, Göster `Text` her ikisi de özelliklerini <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBlock> aynı kaynak özelliğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="87252-109">In the following example, the highlighted lines of code show that the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="87252-110"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Özelliği <xref:System.Windows.Controls.TextBox> bağlama ayarlanmış <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="87252-110">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 <span data-ttu-id="87252-111">Sonuç olarak, <xref:System.Windows.Controls.TextBlock> (kaynak değiştiğinden) metne kullanıcının girdiği aynı metni gösterir <xref:System.Windows.Controls.TextBox>örnek aşağıdaki ekran görüntüsü tarafından gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="87252-111">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 <span data-ttu-id="87252-112">![Basit veri bağlama örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span><span class="sxs-lookup"><span data-stu-id="87252-112">![Simple data binding sample screen shot](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span></span>  
  
 <span data-ttu-id="87252-113">Bir iletişim kutusu veya kullanıcı tarafından düzenlenebilir bir forma sahip ve kullanıcı alanları düzenleme tamamlandı ve "Tamam" seçeneğine tıklar kadar kaynak güncelleştirmelerinin erteleneceği istediğiniz, ayarlayabileceğiniz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bağlamaları için değerini <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="87252-113">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="87252-114">Ayarladığınızda <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değeri <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, uygulama çağırdığında kaynak değeri yalnızca değiştirir <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="87252-114">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="87252-115">Aşağıdaki örnekte nasıl çağrılacağını gösterir <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> için `itemNameTextBox`:</span><span class="sxs-lookup"><span data-stu-id="87252-115">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="87252-116">Diğer denetimlerin özellikleri için aynı yöntemleri kullanabilirsiniz, ancak diğer özelliklerin çoğu varsayılan olduğunu aklınızda bulundurun <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="87252-116">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="87252-117">Daha fazla bilgi için bkz: <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="87252-117">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87252-118"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Özelliği kaynak güncelleştirmeleri ile ilgilenir ve bu nedenle yalnızca ilgili <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlar.</span><span class="sxs-lookup"><span data-stu-id="87252-118">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="87252-119">İçin <xref:System.Windows.Data.BindingMode.TwoWay> ve <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalarının çalışması için özellik değişikliği bildirimlerini sağlaması kaynak nesnesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="87252-119">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="87252-120">Daha fazla bilgi için bu konudaki bildirdi örnekleri başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87252-120">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="87252-121">Ayrıca, bakabilirsiniz [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="87252-121">In addition, you can look at [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87252-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87252-122">See Also</span></span>  
 [<span data-ttu-id="87252-123">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="87252-123">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

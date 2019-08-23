---
title: 'Nasıl yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956068"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="e0773-102">Nasıl yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma</span><span class="sxs-lookup"><span data-stu-id="e0773-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="e0773-103"><xref:System.Windows.Forms.BindingSource> Bileşenini kullanarak formlar arasında kolayca veri paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0773-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="e0773-104">Örneğin, veri kaynağı verilerini özetleyen bir salt biçimli form ve veri kaynağında seçili olan öğe hakkında ayrıntılı bilgi içeren başka bir düzenlenebilir form görüntülenmesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0773-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="e0773-105">Bu örnek, bu senaryoyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0773-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0773-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0773-106">Example</span></span>  
 <span data-ttu-id="e0773-107">Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.BindingSource> ve onun bağlantılı verilerinin formlar arasında nasıl paylaşılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0773-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="e0773-108">Bu örnekte, paylaşılan <xref:System.Windows.Forms.BindingSource> alt formun oluşturucusuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e0773-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="e0773-109">Alt form, kullanıcının ana formda seçili olan öğenin verilerini düzenlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0773-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0773-110"><xref:System.Windows.Forms.BindingSource> Bileşenin olayı, iki formun eşitlenmiş kalmasını sağlamak için örnekte işlenir. <xref:System.Windows.Forms.BindingSource.BindingComplete></span><span class="sxs-lookup"><span data-stu-id="e0773-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="e0773-111">Bunun neden yapıldığı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Aynı veri kaynağıyla bağlantılı birden çok denetimin eşitlenmiş](../multiple-controls-bound-to-data-source-synchronized.md)kalmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e0773-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0773-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e0773-112">Compiling the Code</span></span>  
 <span data-ttu-id="e0773-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e0773-113">This example requires:</span></span>  
  
- <span data-ttu-id="e0773-114">Sisteme, System. Windows. Forms, System. Drawing, System. Data ve System. xml derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e0773-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0773-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0773-115">See also</span></span>

- [<span data-ttu-id="e0773-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e0773-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="e0773-117">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="e0773-117">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="e0773-118">Nasıl yapılır: Veri bağlamada oluşan hataları ve özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="e0773-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)

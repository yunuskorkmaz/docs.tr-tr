---
title: Denetimi bir türe bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744993"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="5628b-102">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="5628b-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="5628b-103">Verilerle etkileşime geçen denetimleri oluştururken, bazen bir denetimi bir nesne yerine bir türe bağlamayı gerekli bulacaktır.</span><span class="sxs-lookup"><span data-stu-id="5628b-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="5628b-104">Bu durum özellikle tasarım zamanında, verilerin kullanılamadığı durumlarda ortaya çıkar, ancak veri bağlantılı denetimleriniz, bir türün ortak arabiriminden bilgi görüntülemeye hala gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="5628b-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="5628b-105">Örneğin, bir Web hizmeti tarafından kullanıma sunulan bir nesneye <xref:System.Windows.Forms.DataGridView> denetimi bağlayabilir ve <xref:System.Windows.Forms.DataGridView> denetiminin sütunlarını tasarım zamanında özel bir türün üye adlarıyla etiketlemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5628b-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="5628b-106"><xref:System.Windows.Forms.BindingSource> bileşeniyle bir denetimi kolayca bir türe bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5628b-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5628b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5628b-107">Example</span></span>  
 <span data-ttu-id="5628b-108">Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.DataGridView> denetiminin bir <xref:System.Windows.Forms.BindingSource> bileşeni kullanılarak özel bir türe nasıl bağlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5628b-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="5628b-109">Örneği çalıştırdığınızda <xref:System.Windows.Forms.DataGridView>, denetimin verilerle doldurulmadan önce, bir `Customer` nesnesinin özelliklerini yansıtan sütunlar etiketli olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5628b-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="5628b-110">Örneğin, <xref:System.Windows.Forms.DataGridView> denetimine veri eklemek için bir müşteri Ekle düğmesi vardır.</span><span class="sxs-lookup"><span data-stu-id="5628b-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5628b-111">Düğmeye tıkladığınızda, <xref:System.Windows.Forms.BindingSource>yeni bir `Customer` nesnesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="5628b-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="5628b-112">Gerçek dünyada bir senaryoda veriler, bir Web hizmeti veya başka bir veri kaynağı çağrısıyla elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="5628b-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5628b-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5628b-113">Compiling the Code</span></span>  
 <span data-ttu-id="5628b-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5628b-114">This example requires:</span></span>  
  
- <span data-ttu-id="5628b-115">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="5628b-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5628b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5628b-116">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="5628b-117">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="5628b-117">BindingSource Component</span></span>](bindingsource-component.md)

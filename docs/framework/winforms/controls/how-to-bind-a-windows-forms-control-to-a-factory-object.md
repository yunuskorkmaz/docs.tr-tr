---
title: Denetimi bir fabrika nesnesine bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745085"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="72782-102">Nasıl yapılır: Windows Forms Denetimini Bir Fabrika Nesnesine Bağlama</span><span class="sxs-lookup"><span data-stu-id="72782-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="72782-103">Verilerle etkileşime geçen denetimleri oluştururken, bazen başka nesneler üreten bir nesne veya yönteme denetim bağlamayı gerekli bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72782-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="72782-104">Bu tür bir nesne veya yöntem fabrika olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="72782-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="72782-105">Veri kaynağınız, örneğin, bellek veya tür bir nesne yerine bir yöntem çağrısından dönüş değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="72782-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="72782-106">Kaynak bir koleksiyon döndürdüğü sürece bu tür veri kaynağına bir denetim bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72782-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="72782-107"><xref:System.Windows.Forms.BindingSource> denetimini kullanarak bir denetimi bir fabrika nesnesine kolayca bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72782-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72782-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="72782-108">Example</span></span>  
 <span data-ttu-id="72782-109">Aşağıdaki örnek, bir <xref:System.Windows.Forms.DataGridView> denetiminin bir <xref:System.Windows.Forms.BindingSource> denetimi kullanılarak bir fabrika yöntemine nasıl bağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="72782-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="72782-110">Fabrika yöntemine `GetOrdersByCustomerId`adı verilir ve Northwind veritabanındaki belirli bir müşteri için tüm siparişler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="72782-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72782-111">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="72782-111">Compiling the Code</span></span>  
 <span data-ttu-id="72782-112">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="72782-112">This example requires:</span></span>  
  
- <span data-ttu-id="72782-113">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="72782-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72782-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72782-114">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="72782-115">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="72782-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="72782-116">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="72782-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

---
title: 'Nasıl yapılır: BindingSource ve Resetıtem metodunu kullanarak değişiklik bildirimleri Yükselt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 50d2203638363831d236a6add7c6f4ba4fbebf4b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644831"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a><span data-ttu-id="4b767-102">Nasıl yapılır: BindingSource ve Resetıtem metodunu kullanarak değişiklik bildirimleri Yükselt</span><span class="sxs-lookup"><span data-stu-id="4b767-102">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>
<span data-ttu-id="4b767-103">Öğeleri değiştirildi, eklendiğinde veya bazı veri kaynakları, denetimler için değişiklik bildirimleri geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="4b767-103">Some data sources for your controls do not raise change notifications when items are changed, added, or deleted.</span></span> <span data-ttu-id="4b767-104">İle <xref:System.Windows.Forms.BindingSource> bileşeni gibi veri kaynaklarına bağlamak ve bir değişiklik bildirimi kodunuzdan Yükselt.</span><span class="sxs-lookup"><span data-stu-id="4b767-104">With the <xref:System.Windows.Forms.BindingSource> component, you can bind to such data sources and raise a change notification from your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b767-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b767-105">Example</span></span>  
 <span data-ttu-id="4b767-106">Bu formu kullanmayı gösterir. bir <xref:System.Windows.Forms.BindingSource> listeye bağlamak için bileşen bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="4b767-106">This form demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind a list to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="4b767-107">Listenin değişiklik bildirimleri geçirmemesi böylece <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metodunda <xref:System.Windows.Forms.BindingSource> listesindeki bir öğe değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4b767-107">The list does not raise change notifications, so the <xref:System.Windows.Forms.BindingSource.ResetItem%2A> method on the <xref:System.Windows.Forms.BindingSource> is called when an item in the list is changed.</span></span> <span data-ttu-id="4b767-108">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="4b767-108">.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b767-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4b767-109">Compiling the Code</span></span>  
 <span data-ttu-id="4b767-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4b767-110">This example requires:</span></span>  
  
-   <span data-ttu-id="4b767-111">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="4b767-111">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4b767-112">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4b767-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4b767-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b767-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="4b767-114">Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="4b767-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b767-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b767-115">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="4b767-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="4b767-116">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="4b767-117">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="4b767-117">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)

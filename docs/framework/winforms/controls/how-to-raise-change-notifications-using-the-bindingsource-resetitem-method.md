---
title: 'Nasıl yapılır: BindingSource ve ResetItem Yöntemini Kullanarak Değişiklik Bildirimleri Verme'
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
ms.openlocfilehash: 68073f245e1a2eb18a277d7011ca0183dabb3724
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913152"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a><span data-ttu-id="0dfec-102">Nasıl yapılır: BindingSource ve ResetItem Yöntemini Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="0dfec-102">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>
<span data-ttu-id="0dfec-103">Öğeleri değiştirildi, eklendiğinde veya bazı veri kaynakları, denetimler için değişiklik bildirimleri geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="0dfec-103">Some data sources for your controls do not raise change notifications when items are changed, added, or deleted.</span></span> <span data-ttu-id="0dfec-104">İle <xref:System.Windows.Forms.BindingSource> bileşeni gibi veri kaynaklarına bağlamak ve bir değişiklik bildirimi kodunuzdan Yükselt.</span><span class="sxs-lookup"><span data-stu-id="0dfec-104">With the <xref:System.Windows.Forms.BindingSource> component, you can bind to such data sources and raise a change notification from your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dfec-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dfec-105">Example</span></span>  
 <span data-ttu-id="0dfec-106">Bu formu kullanmayı gösterir. bir <xref:System.Windows.Forms.BindingSource> listeye bağlamak için bileşen bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0dfec-106">This form demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind a list to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0dfec-107">Listenin değişiklik bildirimleri geçirmemesi böylece <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metodunda <xref:System.Windows.Forms.BindingSource> listesindeki bir öğe değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0dfec-107">The list does not raise change notifications, so the <xref:System.Windows.Forms.BindingSource.ResetItem%2A> method on the <xref:System.Windows.Forms.BindingSource> is called when an item in the list is changed.</span></span> <span data-ttu-id="0dfec-108">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="0dfec-108">.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0dfec-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0dfec-109">Compiling the Code</span></span>  
 <span data-ttu-id="0dfec-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0dfec-110">This example requires:</span></span>  
  
- <span data-ttu-id="0dfec-111">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="0dfec-111">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0dfec-112">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0dfec-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0dfec-113">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dfec-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dfec-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dfec-114">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="0dfec-115">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="0dfec-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="0dfec-116">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="0dfec-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

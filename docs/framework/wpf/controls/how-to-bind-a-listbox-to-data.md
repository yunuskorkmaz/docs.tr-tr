---
title: 'Nasıl yapılır: Veriye ListBox Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 4dea53a524247d18628b3e7e7b2c06906dced53d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911163"
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="d4ca5-102">Nasıl yapılır: Veriye ListBox Bağlama</span><span class="sxs-lookup"><span data-stu-id="d4ca5-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="d4ca5-103">Bir uygulama geliştiricisi oluşturabilirsiniz <xref:System.Windows.Controls.ListBox> her içeriğini belirtmeden denetimleri <xref:System.Windows.Controls.ListBoxItem> ayrı olarak.</span><span class="sxs-lookup"><span data-stu-id="d4ca5-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="d4ca5-104">Veri bağlama, tek tek öğelerine veri bağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4ca5-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="d4ca5-105">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.ListBox> , doldurur <xref:System.Windows.Controls.ListBoxItem> adlı bir veri kaynağına veri bağlama göre öğeleri *renkleri*.</span><span class="sxs-lookup"><span data-stu-id="d4ca5-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="d4ca5-106">Bu durumda kullanmak için gerekli değil <xref:System.Windows.Controls.ListBoxItem> her öğenin içeriğini belirtmek için etiketler.</span><span class="sxs-lookup"><span data-stu-id="d4ca5-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4ca5-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4ca5-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d4ca5-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4ca5-108">See also</span></span>

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [<span data-ttu-id="d4ca5-109">Denetimler</span><span class="sxs-lookup"><span data-stu-id="d4ca5-109">Controls</span></span>](../advanced/optimizing-performance-controls.md)

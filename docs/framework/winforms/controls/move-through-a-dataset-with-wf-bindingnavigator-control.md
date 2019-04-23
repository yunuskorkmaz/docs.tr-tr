---
title: 'Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile DataSet içinde Hareket Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d76c2e5882c9df94674294da00ba446dfbfd2b3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086526"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="24b69-102">Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile DataSet içinde Hareket Etme</span><span class="sxs-lookup"><span data-stu-id="24b69-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="24b69-103">Veri odaklı uygulamalar oluşturmalarını gibi genellikle veri koleksiyonlarının kullanıcılara görüntülenecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="24b69-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="24b69-104"><xref:System.Windows.Forms.BindingNavigator> Birlikte denetim <xref:System.Windows.Forms.BindingSource> bileşeni, bir koleksiyon içinde taşıma ve öğeleri sıralı olarak görüntülemek için kolay ve Genişletilebilir bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="24b69-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24b69-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="24b69-105">Example</span></span>  
 <span data-ttu-id="24b69-106">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.BindingNavigator> veri taşımak için denetimi.</span><span class="sxs-lookup"><span data-stu-id="24b69-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="24b69-107">Küme içindeki bir <xref:System.Data.DataView>, bağlı bir <xref:System.Windows.Forms.TextBox> denetimini bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="24b69-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24b69-108">Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="24b69-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="24b69-109">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="24b69-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="24b69-110">Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="24b69-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24b69-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="24b69-111">Compiling the Code</span></span>  
 <span data-ttu-id="24b69-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="24b69-112">This example requires:</span></span>  
  
-   <span data-ttu-id="24b69-113">Sistem, System.Data System.Drawing, System.Windows.Forms ve System.Xml derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="24b69-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="24b69-114">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="24b69-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="24b69-115">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24b69-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b69-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24b69-116">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="24b69-117">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="24b69-117">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="24b69-118">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="24b69-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="24b69-119">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="24b69-119">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

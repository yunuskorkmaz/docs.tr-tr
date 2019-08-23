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
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952690"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="e4971-102">Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile DataSet içinde Hareket Etme</span><span class="sxs-lookup"><span data-stu-id="e4971-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="e4971-103">Veri odaklı uygulamalar oluştururken, genellikle kullanıcılara veri koleksiyonlarını görüntülemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4971-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="e4971-104"><xref:System.Windows.Forms.BindingSource> Bileşeniyle birlikte denetim, bir koleksiyon içinde gezinmek ve öğeleri sıralı olarak görüntülemek için uygun ve Genişletilebilir <xref:System.Windows.Forms.BindingNavigator> bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4971-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4971-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4971-105">Example</span></span>  
 <span data-ttu-id="e4971-106">Aşağıdaki kod örneği, verilerin nasıl taşınacağı hakkında bir <xref:System.Windows.Forms.BindingNavigator> denetimin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e4971-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="e4971-107">Küme, <xref:System.Data.DataView> bileşeni<xref:System.Windows.Forms.BindingSource> olan bir <xref:System.Windows.Forms.TextBox> denetime bağlantılı olan ' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="e4971-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4971-108">Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e4971-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="e4971-109">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e4971-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="e4971-110">Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="e4971-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4971-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e4971-111">Compiling the Code</span></span>  
 <span data-ttu-id="e4971-112">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e4971-112">This example requires:</span></span>  
  
- <span data-ttu-id="e4971-113">System, System. Data, System. Drawing, System. Windows. Forms ve System. xml derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="e4971-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4971-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4971-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="e4971-115">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="e4971-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="e4971-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e4971-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="e4971-117">Nasıl yapılır: Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="e4971-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

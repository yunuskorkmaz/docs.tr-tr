---
title: BindingNavigator denetimiyle bir veri kümesi Içinde geçiş yapın
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 73a102da74a3a2a00b5042331cffcaf3d858ea5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742158"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="19e08-102">Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile DataSet içinde Hareket Etme</span><span class="sxs-lookup"><span data-stu-id="19e08-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="19e08-103">Veri odaklı uygulamalar oluştururken, genellikle kullanıcılara veri koleksiyonlarını görüntülemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="19e08-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="19e08-104"><xref:System.Windows.Forms.BindingSource> bileşeniyle birlikte <xref:System.Windows.Forms.BindingNavigator> denetimi, bir koleksiyon içinde gezinmek ve öğeleri sıralı olarak görüntülemek için uygun ve genişletilebilir bir çözüm sunar.</span><span class="sxs-lookup"><span data-stu-id="19e08-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19e08-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="19e08-105">Example</span></span>  
 <span data-ttu-id="19e08-106">Aşağıdaki kod örneği, veri üzerinden geçmek için <xref:System.Windows.Forms.BindingNavigator> denetimini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="19e08-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="19e08-107">Küme, bir <xref:System.Windows.Forms.BindingSource> bileşeniyle <xref:System.Windows.Forms.TextBox> denetimine bağlantılı olan bir <xref:System.Data.DataView>bulunur.</span><span class="sxs-lookup"><span data-stu-id="19e08-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19e08-108">Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="19e08-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="19e08-109">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="19e08-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="19e08-110">Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="19e08-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="19e08-111">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="19e08-111">Compiling the Code</span></span>  
 <span data-ttu-id="19e08-112">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="19e08-112">This example requires:</span></span>  
  
- <span data-ttu-id="19e08-113">System, System. Data, System. Drawing, System. Windows. Forms ve System. xml derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="19e08-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e08-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19e08-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="19e08-115">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="19e08-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="19e08-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="19e08-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="19e08-117">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="19e08-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

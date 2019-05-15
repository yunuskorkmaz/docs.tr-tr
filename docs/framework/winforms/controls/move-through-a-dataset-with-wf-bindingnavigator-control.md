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
ms.openlocfilehash: 81b4d574d9fc99f0f002da3e47d81ed17cf8e739
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588641"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="07685-102">Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile DataSet içinde Hareket Etme</span><span class="sxs-lookup"><span data-stu-id="07685-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="07685-103">Veri odaklı uygulamalar oluşturmalarını gibi genellikle veri koleksiyonlarının kullanıcılara görüntülenecek gerekir.</span><span class="sxs-lookup"><span data-stu-id="07685-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="07685-104"><xref:System.Windows.Forms.BindingNavigator> Birlikte denetim <xref:System.Windows.Forms.BindingSource> bileşeni, bir koleksiyon içinde taşıma ve öğeleri sıralı olarak görüntülemek için kolay ve Genişletilebilir bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="07685-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07685-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="07685-105">Example</span></span>  
 <span data-ttu-id="07685-106">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.Windows.Forms.BindingNavigator> veri taşımak için denetimi.</span><span class="sxs-lookup"><span data-stu-id="07685-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="07685-107">Küme içindeki bir <xref:System.Data.DataView>, bağlı bir <xref:System.Windows.Forms.TextBox> denetimini bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="07685-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07685-108">Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="07685-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="07685-109">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="07685-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="07685-110">Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="07685-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07685-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="07685-111">Compiling the Code</span></span>  
 <span data-ttu-id="07685-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="07685-112">This example requires:</span></span>  
  
- <span data-ttu-id="07685-113">Sistem, System.Data System.Drawing, System.Windows.Forms ve System.Xml derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="07685-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07685-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07685-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="07685-115">BindingNavigator Denetimi</span><span class="sxs-lookup"><span data-stu-id="07685-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="07685-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="07685-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="07685-117">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="07685-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

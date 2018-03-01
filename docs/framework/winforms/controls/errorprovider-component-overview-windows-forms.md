---
title: "ErrorProvider Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 589735156ad4d6d639c2449d6bd693e2b3a32d50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="errorprovider-component-overview-windows-forms"></a><span data-ttu-id="1a195-102">ErrorProvider Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1a195-102">ErrorProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="1a195-103">Windows Forms [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) bileşen bir form veya denetim kullanıcı girdisi doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a195-103">The Windows Forms [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) component is used to validate user input on a form or control.</span></span> <span data-ttu-id="1a195-104">Genellikle, bir form üzerinde kullanıcı girişini doğrulama veya dataset içindeki hataları görüntüleme ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a195-104">It is typically used in conjunction with validating user input on a form, or displaying errors within a dataset.</span></span> <span data-ttu-id="1a195-105">Bir ileti kutusu kapatıldıktan sonra hata iletisi artık görünür olmadığı için bir hata sağlayıcısı bir hata iletisi bir ileti kutusu görüntüleme daha daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="1a195-105">An error provider is a better alternative than displaying an error message in a message box, because once a message box is dismissed, the error message is no longer visible.</span></span> <span data-ttu-id="1a195-106"><xref:System.Windows.Forms.ErrorProvider> Bileşen bir hata simgesi görüntüler (![ErrorProvider simgesi](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) kullanıcı üzerinden fare işaretçisini getirdiğinde metin kutusu gibi; ilgili denetim yanındaki hata simgesi, araç ipucu, hata iletisi dizesi gösteren görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1a195-106">The <xref:System.Windows.Forms.ErrorProvider> component displays an error icon (![ErrorProvider icon](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) next to the relevant control, such as a text box; when the user positions the mouse pointer over the error icon, a ToolTip appears, showing the error message string.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="1a195-107">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="1a195-107">Key Properties</span></span>  
 <span data-ttu-id="1a195-108"><xref:System.Windows.Forms.ErrorProvider> Bileşenin anahtar özellikleri <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, ve <xref:System.Windows.Forms.ErrorProvider.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a195-108">The <xref:System.Windows.Forms.ErrorProvider> component's key properties are <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, and <xref:System.Windows.Forms.ErrorProvider.Icon%2A>.</span></span> <span data-ttu-id="1a195-109">Kullanırken <xref:System.Windows.Forms.ErrorProvider> verilere bağlı denetimler ile bileşen <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliği sırada bir hata simgesi formda göstermek için bileşeni için uygun bir kapsayıcı için (genellikle Windows formu) ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a195-109">When using <xref:System.Windows.Forms.ErrorProvider> component with data-bound controls, the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property must be set to the appropriate container (usually the Windows Form) in order for the component to display an error icon on the form.</span></span> <span data-ttu-id="1a195-110">Bileşen Tasarımcısı'nda eklendiğinde <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliğini içeren formun ayarlayın; kodda denetimi eklerseniz, kendiniz ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a195-110">When the component is added in the designer, the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property is set to the containing form; if you add the control in code, you must set it yourself.</span></span>  
  
 <span data-ttu-id="1a195-111"><xref:System.Windows.Forms.ErrorProvider.Icon%2A> Özelliği, varsayılan yerine bir özel hata simgesi için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1a195-111">The <xref:System.Windows.Forms.ErrorProvider.Icon%2A> property can be set to a custom error icon instead of the default.</span></span> <span data-ttu-id="1a195-112">Zaman <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> özelliği ayarlanmış <xref:System.Windows.Forms.ErrorProvider> bileşeni, bir veri kümesi için hata iletileri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a195-112">When the <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> property is set, the <xref:System.Windows.Forms.ErrorProvider> component can display error messages for a dataset.</span></span> <span data-ttu-id="1a195-113">Anahtar yöntemi <xref:System.Windows.Forms.ErrorProvider> bileşeni <xref:System.Windows.Forms.ErrorProvider.SetError%2A> hata ileti dizesi belirtir ve hata simgesi göründüğü yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1a195-113">The key method of the <xref:System.Windows.Forms.ErrorProvider> component is the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method, which specifies the error message string and where the error icon should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a195-114"><xref:System.Windows.Forms.ErrorProvider> Bileşen erişilebilirlik istemciler için yerleşik destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="1a195-114">The <xref:System.Windows.Forms.ErrorProvider> component does not provide built-in support for accessibility clients.</span></span> <span data-ttu-id="1a195-115">Bu bileşen kullanırken, uygulamanızın erişilebilir olması için bir ek, erişilebilir geri bildirim mekanizması sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a195-115">To make your application accessible when using this component, you must provide an additional, accessible feedback mechanism.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a195-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a195-116">See Also</span></span>  
 <xref:System.Windows.Forms.ErrorProvider>  
 [<span data-ttu-id="1a195-117">Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1a195-117">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [<span data-ttu-id="1a195-118">Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1a195-118">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)

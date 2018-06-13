---
title: 'Nasıl yapılır: PropertyNameChanged Desenini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 775a27b1b4ba8143e297a3c4d323356a304073a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536752"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="05efc-102">Nasıl yapılır: PropertyNameChanged Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="05efc-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="05efc-103">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir *PropertyName*değiştirilen özel bir denetim deseni.</span><span class="sxs-lookup"><span data-stu-id="05efc-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="05efc-104">Windows Forms veri bağlama altyapısı ile kullanılan özel denetimler uygulamak, bu deseni uygular.</span><span class="sxs-lookup"><span data-stu-id="05efc-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05efc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="05efc-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="05efc-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="05efc-106">Compiling the Code</span></span>  
 <span data-ttu-id="05efc-107">Önceki kod örneğinde derlemek için:</span><span class="sxs-lookup"><span data-stu-id="05efc-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="05efc-108">Kod bir boş kod dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="05efc-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="05efc-109">Özel denetim içeren bir Windows formunda kullanmalısınız bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05efc-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05efc-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05efc-110">See Also</span></span>  
 [<span data-ttu-id="05efc-111">Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="05efc-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [<span data-ttu-id="05efc-112">Windows Forms Veri Bağlamada Bildirimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="05efc-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="05efc-113">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="05efc-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)

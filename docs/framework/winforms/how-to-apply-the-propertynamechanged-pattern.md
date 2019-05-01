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
ms.openlocfilehash: 36670eee6235277a7fe98770192df9ae05d3dd03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966822"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="8a933-102">Nasıl yapılır: PropertyNameChanged Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="8a933-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="8a933-103">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir *PropertyName*değiştirilen deseni bir özel denetim için.</span><span class="sxs-lookup"><span data-stu-id="8a933-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="8a933-104">Windows Forms veri bağlama altyapısı ile kullanılan özel denetimleri uyguladığınızda bu düzeni uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8a933-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a933-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a933-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a933-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8a933-106">Compiling the Code</span></span>  
 <span data-ttu-id="8a933-107">Önceki kod örneğini derlemek için:</span><span class="sxs-lookup"><span data-stu-id="8a933-107">To compile the previous code example:</span></span>  
  
- <span data-ttu-id="8a933-108">Kodu bir boş bir kod dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="8a933-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="8a933-109">Özel denetim içeren bir Windows formunda kullanmalısınız bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8a933-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a933-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a933-110">See also</span></span>

- [<span data-ttu-id="8a933-111">Nasıl yapılır: INotifyPropertyChanged arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="8a933-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)
- [<span data-ttu-id="8a933-112">Windows Forms Veri Bağlamada Bildirimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="8a933-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="8a933-113">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="8a933-113">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)

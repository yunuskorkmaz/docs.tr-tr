---
title: "Nasıl yapılır: PropertyNameChanged Desenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f53dd2fdaa622e022f49c153b6dbc83030ae791
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="250f2-102">Nasıl yapılır: PropertyNameChanged Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="250f2-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="250f2-103">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir *PropertyName*değiştirilen özel bir denetim deseni.</span><span class="sxs-lookup"><span data-stu-id="250f2-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="250f2-104">Windows Forms veri bağlama altyapısı ile kullanılan özel denetimler uygulamak, bu deseni uygular.</span><span class="sxs-lookup"><span data-stu-id="250f2-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="250f2-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="250f2-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="250f2-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="250f2-106">Compiling the Code</span></span>  
 <span data-ttu-id="250f2-107">Önceki kod örneğinde derlemek için:</span><span class="sxs-lookup"><span data-stu-id="250f2-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="250f2-108">Kod bir boş kod dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="250f2-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="250f2-109">Özel denetim içeren bir Windows formunda kullanmalısınız bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="250f2-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="250f2-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="250f2-110">See Also</span></span>  
 [<span data-ttu-id="250f2-111">Nasıl yapılır: INotifyPropertyChanged arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="250f2-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [<span data-ttu-id="250f2-112">Windows Forms veri bağlamada bildirimi değiştirme</span><span class="sxs-lookup"><span data-stu-id="250f2-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="250f2-113">Windows Forms veri bağlama</span><span class="sxs-lookup"><span data-stu-id="250f2-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)

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
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Nasıl yapılır: PropertyNameChanged Desenini Uygulama
Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir *PropertyName*değiştirilen özel bir denetim deseni. Windows Forms veri bağlama altyapısı ile kullanılan özel denetimler uygulamak, bu deseni uygular.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki kod örneğinde derlemek için:  
  
-   Kod bir boş kod dosyasına yapıştırın. Özel denetim içeren bir Windows formunda kullanmalısınız bir `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: INotifyPropertyChanged arabirimini uygulama](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [Windows Forms veri bağlamada bildirimi değiştirme](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Windows Forms veri bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)

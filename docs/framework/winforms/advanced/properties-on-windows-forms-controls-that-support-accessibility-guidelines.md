---
title: "Windows Forms Denetimlerinde Erişilebilirlik Yönergelerini Destekleyen Özellikler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ca18b35b90b028054e68a0a14fecc819a6c20b9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Windows Forms Denetimlerinde Erişilebilirlik Yönergelerini Destekleyen Özellikler
Windows Forms için standart araç çubuğu denetimleri klavye odağını gösterme ve ekran öğeleri gösterme dahil olmak üzere erişilebilirlik yönergelerini çoğunu destekler.  
  
## <a name="planning-ahead-for-accessibility"></a>Erişilebilirlik için planlama  
 Denetimleri özellikler aşağıdaki tabloda gösterildiği gibi diğer erişilebilirlik yönergelerini desteklemek için kullanılabilir. Ayrıca, menüler program özellikleri erişim sağlamak için kullanmalısınız.  
  
|Denetim özelliği|Erişilebilirlik konuları|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Açıklama, ekran okuyucular gibi erişilebilirlik Yardımcıları bildirilir. Erişilebilirlik yardımları özelleştirilmiş programlardır ve engelli kişilere yardımcı aygıtları bilgisayarlar daha etkili bir şekilde kullanın.|  
|AccessibleName|Erişilebilirlik yardımları bildirilecek adı.|  
|AccessibleRole|Kullanıcı arabirimi öğesinde kullanımını açıklar.|  
|TabIndex|Formun duyarlı bir gezinme yol oluşturur. Metin kutuları, hemen sekme sırası önünde yer bunların ilişkili etiketi olması gibi iç etiketleri olmadan denetimler önemlidir.|  
|Metin|Erişim tuşları oluşturma için "&" karakterini kullanın. Erişim tuşlarını kullanarak özellikleri belgelenen Klavye erişimi sağlama bir parçasıdır.|  
|Yazı tipi boyutu|Yazı tipi boyutu ayarlanabilir değilse, sonra da 10 noktası ya da daha büyük ayarlanmalıdır. Forma bundan sonra eklenen tüm denetimler, formun yazı tipi boyutunu ayarladıktan sonra aynı boyuta sahip olur.|  
|ForeColor|Bu özellik varsayılan olarak ayarlanırsa, kullanıcının renk tercihlerini formda kullanılır.|  
|Arka plan rengi|Bu özellik varsayılan olarak ayarlanırsa, kullanıcının renk tercihlerini formda kullanılır.|  
|BackgroundImage|Bu özellik metin daha okunabilir hale için boş bırakın.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: erişilebilir bir Windows tabanlı uygulama oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)

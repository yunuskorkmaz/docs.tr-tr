---
title: Windows Forms Denetimlerinde Erişilebilirlik Yönergelerini Destekleyen Özellikler
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: b3f10fe472e449d39385facdbc716cba9b3f7382
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183787"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Windows Forms Denetimlerinde Erişilebilirlik Yönergelerini Destekleyen Özellikler
Standart araç kutusunda Windows Forms denetimlerinde erişilebilirlik yönergelerini klavye odağı gösterme ve ekran öğeleri gösterme dahil olmak üzere, çoğunu destekler.  
  
## <a name="planning-ahead-for-accessibility"></a>Erişilebilirlik için planlama  
 Denetim özellikleri, aşağıdaki tabloda gösterildiği gibi diğer erişilebilirlik yönergeleri desteklemek için kullanılabilir. Ayrıca, program özellikleri erişim sağlamak için menü kullanmalısınız.  
  
|Denetim özelliği|Erişilebilirlik konuları|  
|----------------------|--------------------------------------|  
|AccessibleDescription|Açıklama, Erişilebilirlik Yardımcıları ekran okuyucular gibi bildirilir. Erişilebilirlik yardımları özel programları ve engelli kişilerin yardımcı aygıtları bilgisayarlar daha etkili bir şekilde kullanır.|  
|AccessibleName|Erişilebilirlik yardımları için bildirilen ad.|  
|AccessibleRole|Kullanıcı arabirimi öğesinde kullanımını açıklar.|  
|TabIndex|Formu aracılığıyla mantıklı bir gezinti yolu oluşturur. İç etiketsiz sekme sırasının kendilerinden hemen kendi ilişkili etiket için metin kutuları gibi denetimler için önemlidir.|  
|Metin|Erişim anahtarları oluşturmak için "&" karakterini kullanın. Erişim anahtarlarını kullanarak, belgelenmiş klavye erişim özellikleri sağlayan parçasıdır.|  
|Yazı tipi boyutu|Yazı tipi boyutu ayarlanabilir değilse, sonra da 10 noktalarına ya da daha büyük ayarlanması gerekir. Formun yazı tipi boyutu ayarlandıktan sonra forma bundan sonra eklenen tüm denetimlerin aynı boyutta olacaktır.|  
|ForeColor|Bu özellik varsayılan olarak ayarlanırsa kullanıcının rengi tercihlerini formda kullanılır.|  
|Arka plan rengi|Bu özellik varsayılan olarak ayarlanırsa kullanıcının rengi tercihlerini formda kullanılır.|  
|BackgroundImage|Bu özellik, metin daha okunabilir yapmak için boş bırakın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Erişilebilir bir Windows tabanlı uygulama oluşturma](walkthrough-creating-an-accessible-windows-based-application.md)

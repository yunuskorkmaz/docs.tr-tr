---
title: Denetimlerde erişilebilirlik özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: 73d81f5b5f656ed5ef90bdd9b6fe1b3293123f97
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743428"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Windows Forms Denetimlerinde Erişilebilirlik Yönergelerini Destekleyen Özellikler
Windows Forms için Standart araç kutusu üzerindeki denetimler, klavye odağını gösterme ve ekran öğelerini gösterme dahil olmak üzere erişilebilirlik yönergelerinin çoğunu destekler.  
  
## <a name="planning-ahead-for-accessibility"></a>Erişilebilirliği önceden planlama  
 Denetimlerin özellikleri, aşağıdaki tabloda gösterildiği gibi diğer Erişilebilirlik yönergelerini desteklemek için kullanılabilir. Ayrıca, program özelliklerine erişim sağlamak için menüleri kullanmanız gerekir.  
  
|Denetim özelliği|Erişilebilirlik konuları|  
|----------------------|--------------------------------------|  
|Erişilebilir açıklama|Açıklama, ekran okuyucular gibi erişilebilirlik yardımlarına bildirilir. Erişilebilirlik yardımları, Engelli kişilerin bilgisayarları daha verimli bir şekilde kullanmasına yardımcı olan özel programlar ve cihazlardır.|  
|Erişilebilir ad|Erişilebilirlik yardımlarına bildirilecek ad.|  
|Erişilebilir OLE|Kullanıcı arabirimindeki öğesinin kullanımını açıklar.|  
|Atan|Form aracılığıyla bir senerişilebilir gezinme yolu oluşturur. Metin kutuları gibi iç etiketleri olmayan denetimler için, ilgili etiketlerin sekme düzeninde hemen önüne gelmesi önemlidir.|  
|Metin|Erişim tuşları oluşturmak için "&" karakterini kullanın. Erişim tuşlarının kullanılması, özelliklere yönelik belgelenmiş klavye erişimi sağlamanın bir parçasıdır.|  
|Yazı tipi boyutu|Yazı tipi boyutu ayarlanamaz değilse, 10 noktaya veya daha büyük olarak ayarlanmalıdır. Formun yazı tipi boyutu ayarlandıktan sonra, forma eklenen tüm denetimler, bundan sonra aynı boyutta olur.|  
|ForeColor|Bu özellik varsayılan olarak ayarlanırsa, formda kullanıcının renk tercihleri kullanılacaktır.|  
|Rengi|Bu özellik varsayılan olarak ayarlanırsa, formda kullanıcının renk tercihleri kullanılacaktır.|  
|BackgroundImage|Metni daha okunaklı hale getirmek için bu özelliği boş bırakın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma](walkthrough-creating-an-accessible-windows-based-application.md)

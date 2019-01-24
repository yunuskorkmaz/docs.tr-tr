---
title: 'Nasıl yapılır: Uygulama oturumları arasında bir ayarın değerini değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 475e57e8bfdd5f3296c6af0fb20a472c729ea75c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540721"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Nasıl yapılır: Uygulama oturumları arasında bir ayarın değerini değiştirme
Bazen, sonra uygulamayı derlenen ve dağıtılan uygulama oturumları arasında bir ayarın değerini değiştirmek isteyebilirsiniz. Örneğin, bir bağlantı dizesi doğru veritabanı konumunu gösterecek şekilde değiştirmek isteyebilirsiniz. Uygulamayı derlenen ve dağıtılan sonra Tasarım zamanı araçları kullanılamaz olduğundan, ayar değeri el ile dosya değiştirmeniz gerekir.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Uygulama oturumları arasında bir ayarın değerini değiştirmek için  
  
1.  Microsoft Notepad veya bazı diğer metin veya XML Düzenleyicisi'ni kullanarak, uygulamanızla ilişkili .config dosyasını açın.  
  
2.  Değiştirmek istediğiniz ayarı girişini bulun. Aşağıda gösterilen örneğe benzemelidir.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  Ayarınız için yeni bir değer girin ve dosyayı kaydedin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)

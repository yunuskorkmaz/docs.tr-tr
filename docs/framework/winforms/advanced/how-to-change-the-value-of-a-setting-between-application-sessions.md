---
title: 'Nasıl yapılır: Uygulama Oturumları Arasında Bir Ayarın Değerini Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 383f72f223fb92170d16a9538c94e67825009abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Nasıl yapılır: Uygulama Oturumları Arasında Bir Ayarın Değerini Değiştirme
Bazen, sonra uygulama derlenmiş ve dağıtılmış uygulama oturumları arasında bir ayarın değerini değiştirmek isteyebilirsiniz. Örneğin, bir bağlantı dizesi doğru veritabanı konumunu gösterecek şekilde değiştirmek isteyebilirsiniz. Uygulama derlenmiş ve dağıtılan sonra Tasarım zamanı araçları kullanılamaz olduğundan, ayar değeri dosyayı el ile değiştirmeniz gerekir.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Uygulama oturumları arasında bir ayarın değerini değiştirmek için  
  
1.  Microsoft Notepad veya bazı diğer metin veya XML düzenleyicisi kullanarak, uygulamanızla ilişkili .config dosyasını açın.  
  
2.  Değiştirmek istediğiniz ayarı girişini bulun. Aşağıda sunulan örneğe benzemelidir.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  Ayarınız için yeni bir değer yazın ve dosyayı kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)

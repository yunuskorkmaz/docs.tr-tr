---
title: 'Nasıl yapılır: Uygulama Oturumları Arasında Bir Ayarın Değerini Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 95e613cb280813cd75d887d3cf147d7c897bc2e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004438"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Nasıl yapılır: Uygulama Oturumları Arasında Bir Ayarın Değerini Değiştirme
Bazen, sonra uygulamayı derlenen ve dağıtılan uygulama oturumları arasında bir ayarın değerini değiştirmek isteyebilirsiniz. Örneğin, bir bağlantı dizesi doğru veritabanı konumunu gösterecek şekilde değiştirmek isteyebilirsiniz. Uygulamayı derlenen ve dağıtılan sonra Tasarım zamanı araçları kullanılamaz olduğundan, ayar değeri el ile dosya değiştirmeniz gerekir.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Uygulama oturumları arasında bir ayarın değerini değiştirmek için  
  
1. Microsoft Notepad veya bazı diğer metin veya XML Düzenleyicisi'ni kullanarak, uygulamanızla ilişkili .config dosyasını açın.  
  
2. Değiştirmek istediğiniz ayarı girişini bulun. Aşağıda gösterilen örneğe benzemelidir.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3. Ayarınız için yeni bir değer girin ve dosyayı kaydedin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma](using-application-settings-and-user-settings.md)
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)

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
ms.locfileid: "33523416"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="f3819-102">Nasıl yapılır: Uygulama Oturumları Arasında Bir Ayarın Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f3819-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="f3819-103">Bazen, sonra uygulama derlenmiş ve dağıtılmış uygulama oturumları arasında bir ayarın değerini değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3819-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="f3819-104">Örneğin, bir bağlantı dizesi doğru veritabanı konumunu gösterecek şekilde değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3819-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="f3819-105">Uygulama derlenmiş ve dağıtılan sonra Tasarım zamanı araçları kullanılamaz olduğundan, ayar değeri dosyayı el ile değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3819-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="f3819-106">Uygulama oturumları arasında bir ayarın değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f3819-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="f3819-107">Microsoft Notepad veya bazı diğer metin veya XML düzenleyicisi kullanarak, uygulamanızla ilişkili .config dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f3819-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="f3819-108">Değiştirmek istediğiniz ayarı girişini bulun.</span><span class="sxs-lookup"><span data-stu-id="f3819-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="f3819-109">Aşağıda sunulan örneğe benzemelidir.</span><span class="sxs-lookup"><span data-stu-id="f3819-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="f3819-110">Ayarınız için yeni bir değer yazın ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f3819-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3819-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3819-111">See Also</span></span>  
 [<span data-ttu-id="f3819-112">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f3819-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="f3819-113">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f3819-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)

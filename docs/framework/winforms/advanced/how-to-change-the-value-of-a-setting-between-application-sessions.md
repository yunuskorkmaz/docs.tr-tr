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
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="6fb75-102">Nasıl yapılır: Uygulama oturumları arasında bir ayarın değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="6fb75-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="6fb75-103">Bazen, sonra uygulamayı derlenen ve dağıtılan uygulama oturumları arasında bir ayarın değerini değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fb75-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="6fb75-104">Örneğin, bir bağlantı dizesi doğru veritabanı konumunu gösterecek şekilde değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fb75-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="6fb75-105">Uygulamayı derlenen ve dağıtılan sonra Tasarım zamanı araçları kullanılamaz olduğundan, ayar değeri el ile dosya değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fb75-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="6fb75-106">Uygulama oturumları arasında bir ayarın değerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="6fb75-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="6fb75-107">Microsoft Notepad veya bazı diğer metin veya XML Düzenleyicisi'ni kullanarak, uygulamanızla ilişkili .config dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6fb75-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="6fb75-108">Değiştirmek istediğiniz ayarı girişini bulun.</span><span class="sxs-lookup"><span data-stu-id="6fb75-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="6fb75-109">Aşağıda gösterilen örneğe benzemelidir.</span><span class="sxs-lookup"><span data-stu-id="6fb75-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="6fb75-110">Ayarınız için yeni bir değer girin ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6fb75-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb75-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fb75-111">See also</span></span>
- [<span data-ttu-id="6fb75-112">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="6fb75-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="6fb75-113">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6fb75-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)

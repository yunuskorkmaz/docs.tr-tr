---
title: "Etkinlik yerelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccabcda9e26751db80ee7e955458d0eee0cae7e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="activity-localization"></a><span data-ttu-id="b69a4-102">Etkinlik yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="b69a4-102">Activity Localization</span></span>
<span data-ttu-id="b69a4-103">İş akışı uygulamaları ve bileşenleri diğer kültürlere ve dilleri yerelleştirilmiş olma olasılığı varsa, böylece derlemeden yerelleştirilebilir kaynak dizeleri kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b69a4-103">When workflow applications and components have the potential to be localized into other cultures and languages, resource strings should be used so that they can be localized without recompiling.</span></span>  
  
## <a name="activity-localization"></a><span data-ttu-id="b69a4-104">Etkinlik yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="b69a4-104">Activity Localization</span></span>  
 <span data-ttu-id="b69a4-105">Olarak (farklı dillere ve kültürlere için farklı sürümleri de serbest), yerelleştirilmiş olmalıdır tüm uygulamalarla kullanıcıya görüntülenen herhangi bir dizgi değil doğrudan kodunda put, ancak yerine bir kaynak dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="b69a4-105">As with all applications that must be localized (released in different versions for different languages and cultures), any strings that are displayed to the user should not be put directly in code, but rather stored in a resource file.</span></span> <span data-ttu-id="b69a4-106">Dizeler ardından aracılığıyla erişilebilir <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span><span class="sxs-lookup"><span data-stu-id="b69a4-106">The strings can then be accessed through <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span></span> <span data-ttu-id="b69a4-107">Çeşitli dillerde dağıtılmış bir bileşen geliştiriyorsanız, aynı zamanda etkinlik doğrulama iletileri için kullanıcı tanımlı veri, izleme iletileri ve hata iletileri izleme kaynak dizeleri kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="b69a4-107">If you are developing a component that is distributed in several languages, you also want to use resource strings for activity validation messages, user-defined tracking data, tracing messages, and error messages as well.</span></span>  
  
 <span data-ttu-id="b69a4-108">Aşağıdaki alıştırmada bir kaynak dosyasının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b69a4-108">The following exercise demonstrates how to use a resource file.</span></span>  
  
#### <a name="using-resource-files-for-localized-strings"></a><span data-ttu-id="b69a4-109">Yerelleştirilmiş dizeleri için kaynak dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="b69a4-109">Using resource files for localized strings</span></span>  
  
1.  <span data-ttu-id="b69a4-110">İçinde [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], projenize sağ **Çözüm Gezgini** seçip **Ekle...** , **Yeni öğe...** .</span><span class="sxs-lookup"><span data-stu-id="b69a4-110">In [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], right-click your project in **Solution Explorer** and select **Add…**, **New Item…**.</span></span>  
  
2.  <span data-ttu-id="b69a4-111">Seçin **kaynakları dosya** ve ErrorResources.resx dosya adı.</span><span class="sxs-lookup"><span data-stu-id="b69a4-111">Select **Resources File** and name the file ErrorResources.resx.</span></span> <span data-ttu-id="b69a4-112">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b69a4-112">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="b69a4-113">Kaynak dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b69a4-113">Open the resource file.</span></span> <span data-ttu-id="b69a4-114">Yeni bir girdi ile eklemek bir **adı** ErrorString ve bir **değeri** "etkinliği geçerli değil.",</span><span class="sxs-lookup"><span data-stu-id="b69a4-114">Add a new entry with a **Name** of ErrorString and a **Value** of "The activity is not valid."</span></span>  
  
4.  <span data-ttu-id="b69a4-115">Aşağıdakileri ekleyin `using` deyimleri sınıfınıza.</span><span class="sxs-lookup"><span data-stu-id="b69a4-115">Add the following `using` statements to your class.</span></span>  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  <span data-ttu-id="b69a4-116">Bir kaynak yöneticisi projenizde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b69a4-116">Create a resource manager in your project.</span></span>  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  <span data-ttu-id="b69a4-117">Dize, gerekli olduğu Kaynak Yöneticisi'nden alın.</span><span class="sxs-lookup"><span data-stu-id="b69a4-117">Get the string from the resource manager where it is required.</span></span>  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 <span data-ttu-id="b69a4-118">Aşağıdaki kod örneği, yerelleştirilmiş dizeleri kullanmak gösterilmiştir <xref:System.Activities.Activity.CacheMetadata%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b69a4-118">The following code sample demonstrates how to utilize localized strings in the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span>  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```

---
title: Değişken ve Bağımsız Değişken İzleme
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: c5d3fe6626c22184edd83de6aedad8589ab2ef35
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837551"
---
# <a name="variable-and-argument-tracking"></a>Değişken ve Bağımsız Değişken İzleme
Bir iş akışının yürütülmesi izlenirken, verileri ayıklamak genellikle yararlı olur. Bu, bir izleme kaydına erişirken yürütme sonrası ek bağlam sağlar. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]' de, izleme kullanarak bir iş akışındaki herhangi bir etkinliğin kapsamındaki görünür herhangi bir değişkeni veya bağımsız değişkeni ayıklayabilirsiniz. İzleme profilleri, verileri ayıklamayı kolaylaştırır.  
  
## <a name="variables-and-arguments"></a>Değişkenler ve Bağımsız Değişkenler  
 Bir etkinlik bir ActivityStateRecord yayar olduğunda değişkenler ve bağımsız değişkenler ayıklanır.  Değişken, yalnızca etkinliğin kapsamı içindeyse, ayıklama için kullanılabilir. Bir etkinlik içinde Ayıklanacak bir değişken aşağıdaki şekilde belirtilir:  
  
- Değişken adıyla bir değişken belirtilmişse, izleme geçerli etkinliğin içinde ve üst etkinliklerdeki değişkeni arar. Değişken geçerli etkinlik kapsamında ve üst kapsamda aranır.  
  
- Ayıklanacak değişkenler Name = "\*" kullanılarak belirtilmişse, izlenen geçerli etkinliğin içindeki tüm değişkenler ayıklanır. Bu durumda, kapsamdaki ancak üst etkinliklerde tanımlanan değişkenler ayıklanmaz.  
  
 Bağımsız değişkenler ayıklanırken, ayıklanan bağımsız değişkenler etkinliğin durumuna bağlıdır. Bir etkinliğin durumu yürütüldüğü zaman, ayıklama için yalnızca `InArguments` kullanılabilir. Diğer etkinlik durumları (kapalı, hatalı, Iptal edildi) için, tüm bağımsız değişkenler, hem InArguments hem de OutArguments, ayıklama için kullanılabilir.  
  
 Aşağıdaki örnek, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterir. Değişkenler ve bağımsız değişkenler yalnızca bir <xref:System.Activities.Tracking.ActivityStateRecord> ayıklanıp <xref:System.Activities.Tracking.ActivityStateQuery>kullanılarak bir izleme profili içinde abone olunmuş olabilir.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Değişkenler ve bağımsız değişkenler Içinde depolanan bilgileri koruma  
 İzlenen bir değişken veya bağımsız değişken varsayılan olarak WF çalışma zamanı tarafından görünür hale getirilir. Bir iş akışı geliştiricisi, aşağıdaki adımları uygulayarak bu BT 'nin erişmesini koruyabilir:  
  
1. Bir değişkenin değerini şifreleyin.  
  
2. Bir değişkenin veya bağımsız değişkenin ayıklanmasını engellemek için bir izleme profili yazmayı denetleyin.  
  
3. Özel izleme katılımcıları için, WF kodunun değişkenlerde veya bağımsız değişkenlerde depolanan hassas bilgileri açıklamadığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))

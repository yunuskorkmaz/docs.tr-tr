---
title: Özel etkinlik kullanma
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 43addd4e69b7f7ac3ac5cd8e5bcd41397d8f0a67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293331"
---
# <a name="using-a-custom-activity"></a>Özel etkinlik kullanma

<xref:System.Activities.Activity>Veya alt sınıflarından türeten etkinlikler daha büyük iş akışlarına eklenebilir veya doğrudan kodda oluşturulabilir. Bu konuda, kodda veya tasarımcıda oluşturulan iş akışlarında özel etkinliklerin nasıl kullanılacağı açıklanmaktadır.  
  
> [!NOTE]
> Özel etkinlikler tanımlandıkları projede, hem özel etkinlik hem de onu kullanan etkinlik derlenmişse (örn., derleme işlemi tarafından oluşturulan bir örnek oluşturma türü tarafından yüklenir), başvuru etkinliği dinamik olarak yüklenirse (örneğin, ActivityXAMLServices kullanılarak), başvurulan derleme farklı bir projeye yerleştirilmelidir veya tasarımcı tarafından oluşturulan XAML 'in bunu etkinleştirmek için el ile düzenlenmiş olması gerekir.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Bir iş akışı projesine özel etkinlik kullanma  
  
1. Ana bilgisayar projesinden özel etkinliği içeren etkinlik kitaplığı projesine bir başvuru ekleyin.  
  
2. Çözümü derleyin.  
  
3. Tasarımcıda özel etkinliği kullanmak için araç kutusunda özel etkinliğini bulun ve etkinliği tasarımcı yüzeyine sürükleyin.  
  
4. Kodda özel etkinliği kullanmak için özel etkinlik projesine başvuran bir using ifadesini ekleyin ve etkinliğin yeni bir örneğini ' ye geçirin <xref:System.Activities.WorkflowInvoker.Invoke%2A> .

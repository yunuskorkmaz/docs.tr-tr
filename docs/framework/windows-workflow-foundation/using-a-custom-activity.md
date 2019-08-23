---
title: Özel etkinlik kullanma
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 6ca67ef7a8c4330d0182e960fc3fdcce656976a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962217"
---
# <a name="using-a-custom-activity"></a>Özel etkinlik kullanma
Veya alt sınıflarından türeten <xref:System.Activities.Activity> etkinlikler daha büyük iş akışlarına eklenebilir veya doğrudan kodda oluşturulabilir. Bu konuda, kodda veya tasarımcıda oluşturulan iş akışlarında özel etkinliklerin nasıl kullanılacağı açıklanmaktadır.  
  
> [!NOTE]
> Özel etkinlikler tanımlandıkları projede, hem özel etkinlik hem de onu kullanan etkinlik derlendikleri sürece (örneğin, derleme işlemi tarafından oluşturulan bir örnek oluşturma türü tarafından yüklenir), başvuru etkinliği yüklüyse kullanılabilir dinamik olarak (örneğin, ActivityXAMLServices kullanarak), başvurulan derleme farklı bir projeye yerleştirilmelidir veya tasarımcı tarafından oluşturulan XAML 'in bunu etkinleştirmek için el ile düzenlenmesi gerekir.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Bir iş akışı projesine özel etkinlik kullanma  
  
1. Ana bilgisayar projesinden özel etkinliği içeren etkinlik kitaplığı projesine bir başvuru ekleyin.  
  
2. Çözümü oluşturun.  
  
3. Tasarımcıda özel etkinliği kullanmak için araç kutusunda özel etkinliğini bulun ve etkinliği tasarımcı yüzeyine sürükleyin.  
  
4. Kodda özel etkinliği kullanmak için özel etkinlik projesine başvuran bir using ifadesini ekleyin ve etkinliğin yeni bir örneğini ' ye <xref:System.Activities.WorkflowInvoker.Invoke%2A>geçirin.

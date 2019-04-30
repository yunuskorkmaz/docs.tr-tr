---
title: Özel etkinlik kullanma
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 47ddd42168445aa23eaaded6fd19ffe4698e4117
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669582"
---
# <a name="using-a-custom-activity"></a>Özel etkinlik kullanma
Öğesinden türetilen etkinlikleri <xref:System.Activities.Activity> veya alt sınıflara daha büyük iş akışlarına oluşan veya doğrudan kod içinde oluşturulur. Bu konuda, kod veya Tasarımcısı'nda oluşturulan iş akışlarında özel etkinlikler kullanma açıklar.  
  
> [!NOTE]
>  Özel etkinlikler hem özel etkinliği hem de kullandığı etkinlik (yani yapı işlemi tarafından oluşturulan bir instantiating türü tarafından yüklenen) derlenen sürece bunların tanımlandığı, aynı projede kullanılabilir başvuruda bulunan bir etkinlik yüklü ise dinamik olarak (örn ActivityXAMLServices kullanarak), başvurulan derleme farklı bir projede ardından yerleştirilmesi gerektiğini veya tasarımcı tarafından oluşturulan XAML bunu etkinleştirmek için elle düzenlenerek olması gerekir.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Bir iş akışı projesine özel etkinlik kullanma  
  
1. Bir başvuru konağı projeden özel etkinlik içeren etkinlik kitaplığı projeye ekleyin.  
  
2. Çözümü oluşturun.  
  
3. Özel Etkinlik Tasarımcısı'nda kullanmak için özel etkinlik araç kutusunda bulun ve etkinlik tasarımcısının yüzeyine sürükleyin.  
  
4. Kodda özel etkinlik kullanmak için özel etkinlik projesine başvuruda bulunan bir Using deyimi ekleyin ve etkinlik için yeni bir örneğini geçirin <xref:System.Activities.WorkflowInvoker.Invoke%2A>.

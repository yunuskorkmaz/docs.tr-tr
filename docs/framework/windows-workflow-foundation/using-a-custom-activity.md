---
title: "Özel Etkinlik kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cea0e819c79550b27a71957f6d8c2c9badfef7c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-a-custom-activity"></a>Özel Etkinlik kullanma
Öğesinden türetilen etkinlikleri <xref:System.Activities.Activity> veya alt sınıfları büyük iş akışlarıyla birleştirilerek oluşur veya doğrudan kod içinde oluşturulan. Bu konu, kod veya Tasarımcısı'nda oluşturulan iş akışlarında özel etkinlikleri kullanmak açıklar.  
  
> [!NOTE]
>  Özel etkinlikler özel etkinlik ve kullandığı etkinlik (yani yapı işlemi tarafından oluşturulan bir instantiating türü tarafından yüklenen) derlendiğini sürece, bunlar tanımlanan projesinde kullanılabilir başvuru etkinlik yüklerse dinamik olarak (örneğin ActivityXAMLServices kullanarak), sonra farklı bir projedeki başvurulan derlemeyi yerleştirilmelidir veya tasarımcısı tarafından oluşturulan XAML el ile düzenleyebilirsiniz bunu etkinleştirmek için olması gerekir.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Bir iş akışı projeye özel bir aktivite kullanma  
  
1.  Bir başvuru konak projeden özel etkinlik içeren etkinlik kitaplığı projeye ekleyin.  
  
2.  Çözümü oluşturun.  
  
3.  Özel Etkinlik Tasarımcısı'nda kullanmak için özel etkinlik araç kutusunda bulun ve etkinlik Tasarımcı yüzeyine sürükleyin.  
  
4.  Kodda özel etkinlik kullanmak için özel etkinlik projeye başvuruda bulunan bir Using deyimi eklemek ve etkinlik için yeni bir örneğini geçirin <xref:System.Activities.WorkflowInvoker.Invoke%2A>.

---
title: Etkinlik Doğrulamayı Yapılandırma
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 6c971b56e269fbb330bd9ad0a551a9fb9ca01196
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655109"
---
# <a name="configuring-activity-validation"></a>Etkinlik Doğrulamayı Yapılandırma
Etkinlik yazarlar ve kullanıcıları tanımlama ve yürütme öncesi bir etkinliğin yapılandırma hatalarını raporlamak etkinlik doğrulamayı etkinleştirir. Windows Workflow Foundation (WF) aşağıdaki üç tür etkinliği doğrulama sağlar:  
  
- `RequiredArgument` ve `OverloadGroup` öznitelikleri.  
  
- Kesin kod temelli doğrulama.  
  
- Bildirim temelli kısıtlamalar.  
  
 `RequiredArgument` ve `OverloadGroup` öznitelikleri gösteren belirli bağımsız değişkenler bir etkinlikte gereklidir. Kesin kod temelli doğrulama doğrulama kendisi hakkında sağlamaya bir etkinlik için basit bir yol sağlar ve doğrulama etkinliği ve ilişkisini içeren iş akışı ile ilgili bildirim temelli kısıtlamalar etkinleştirin. Bir etkinlik doğrulama gereksinimlerine göre düzgün şekilde yapılandırılmadıysa, doğrulama hataları ve Uyarıları döndürülür. Kapsanan iş akışını iş akışı Tasarımcısı'nı kullanarak oluşturulduysa, doğrulama hataları ve Uyarıları Tasarımcısı'nda görüntülenir. İş akışı iş akışı Tasarımcısı dışında oluşturulursa tüm doğrulama hatalarını iş akışı çalıştırıldığında döndürülür. İş akışını nasıl oluşturulduğuna bakılmaksızın, bir iş akışı doğrulama hataları asla yürütmek için izin verilmez. Bu bölümde, bu tür etkinlik doğrulamayı ve etkinlik doğrulamayı nasıl çağrıldığını'ne genel bakış sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar](required-arguments-and-overload-groups.md)  
 Nasıl kullanılacağını açıklar `RequiredArgument` ve `OverloadGroup` doğrulama sağlamak için öznitelikler.  
  
 [Kesin Kod Temelli Doğrulama](imperative-code-based-validation.md)  
 Kod temelli doğrulama için kullanmayı açıklar <xref:System.Activities.CodeActivity> ve <xref:System.Activities.NativeActivity> etkinlikleri temel.  
  
 [Bildirim Temelli Kısıtlamalar](declarative-constraints.md)  
 Bildirim temelli kısıtlamalar karmaşık etkinlik doğrulama sağlamak için nasıl kullanılacağını açıklar.  
  
 [Etkinlik Doğrulamayı Çağırma](invoking-activity-validation.md)  
 Etkinlik doğrulamayı otomatik olarak ne zaman çağrılır ve doğrulama açıkça çağırmak nasıl ele alır.  
  
## <a name="reference"></a>Başvuru  
  
## <a name="related-sections"></a>İlgili Bölümler

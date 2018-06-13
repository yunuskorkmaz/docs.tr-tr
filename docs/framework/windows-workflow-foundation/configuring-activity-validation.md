---
title: Etkinlik doğrulama yapılandırma
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: e6fa043e0a0a96875319d556c19ab8ee90cd2139
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512606"
---
# <a name="configuring-activity-validation"></a>Etkinlik doğrulama yapılandırma
Etkinlik yazarlar ve kullanıcıları tanımlamak ve hataları yürütülmesinin önce bir etkinliğin yapılandırmasında raporlar etkinlik doğrulamayı etkinleştirir. Windows Workflow Foundation (WF) etkinlik doğrulama aşağıdaki üç türlerini sağlar:  
  
-   `RequiredArgument` ve `OverloadGroup` öznitelikleri.  
  
-   Kesinlik temelli kod tabanlı doğrulama.  
  
-   Bildirim temelli kısıtlamaları.  
  
 `RequiredArgument` ve `OverloadGroup` öznitelikleri gösteren bir etkinlikte bazı bağımsız değişkenler zorunludur. Kesinlik temelli kod tabanlı doğrulama kendisi hakkında doğrulama sağlamak bir etkinlik için basit bir yol sağlar ve doğrulama ve etkinliğini içeren iş akışı ile ilişkisini hakkında bildirim temelli kısıtlamalarını etkinleştirin. Bir etkinlik doğrulama gereksinimlerine göre düzgün şekilde yapılandırılmazsa, doğrulama hataları ve Uyarıları döndürülür. İş Akışı Tasarımcısı'nı kullanarak içeren iş akışı oluşturduysanız, doğrulama hataları ve Uyarıları Tasarımcısı'nda görüntülenir. İş akışını iş akışı Tasarımcısı dışında oluşturulursa, iş akışı çalıştırıldığında herhangi bir doğrulama hatası döndürülür. İş akışının nasıl oluşturulduğuna bakılmaksızın, doğrulama hataları içeren bir iş akışının asla yürütmek için izin verilmez. Bu bölümde, bu tür etkinlik doğrulama ve etkinlik doğrulama nasıl çağrıldığını genel bakış sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 Nasıl kullanılacağını açıklar `RequiredArgument` ve `OverloadGroup` doğrulama sağlamak için öznitelikler.  
  
 [Kesin Kod Temelli Doğrulama](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 Kod tabanlı doğrulama için kullanılacak açıklar <xref:System.Activities.CodeActivity> ve <xref:System.Activities.NativeActivity> etkinlikleri tabanlı.  
  
 [Bildirim Temelli Kısıtlamalar](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 Bildirim temelli kısıtlamaları karmaşık etkinlik doğrulama sağlamak için nasıl kullanılacağını açıklar.  
  
 [Etkinlik Doğrulamayı Çağırma](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 Etkinlik doğrulama otomatik olarak ne zaman çağrılır ve açıkça doğrulamayı çağırmak nasıl anlatılmaktadır.  
  
## <a name="reference"></a>Başvuru  
  
## <a name="related-sections"></a>İlgili Bölümler

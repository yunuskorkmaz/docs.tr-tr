---
title: İş Akışı Barındırma Seçenekleri
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: b0cd9748c28cd6206e1fedffc5772b2849462dba
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487360"
---
# <a name="workflow-hosting-options"></a>İş Akışı Barındırma Seçenekleri
Bir konsol uygulamasında barındırılan iş akışı Windows Workflow Foundation (WF) örnekleri çoğu kullanın, ancak bu gerçek iş akışları için gerçekçi bir senaryo değildir. Gerçek iş uygulamalarını iş akışlarında kalıcı işlemleri yazılan bir Windows hizmeti-geliştirici ya da IIS 7.0 veya AppFabric gibi bir sunucu uygulaması tarafından barındırılacak. Bu yaklaşımların arasındaki farklar aşağıdaki gibidir.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>IIS Windows AppFabric ile iş akışları barındırma  
 AppFabric ile IIS kullanarak iş akışları için tercih edilen ana bilgisayardır. IIS üzerinde tek başına HTTP üzerindeki bağımlılığı kaldırır Windows Etkinleştirme hizmeti AppFabric kullanarak iş akışları için ana bilgisayar uygulamasıdır.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Tek başına bir IIS iş akışları barındırma  
 Yönetim ve izleme çalışan uygulamaların Bakımı kolaylaştıran AppFabric ile kullanılabilen araçları olduğundan kullanarak tek başına bir IIS 7.0, önerilmez. İş akışları yalnızca IIS 7.0 AppFabric için taşıma ile altyapıyla ilgili endişelerini yoksa tek başına barındırılması.  
  
> [!WARNING]
>  IIS 7.0 uygulama havuzu çeşitli nedenlerden dolayı düzenli aralıklarla geri dönüştürür. Bir uygulama havuzu geri dönüştürüldüğünde, IIS eski havuzuna iletileri kabul etmeye durdurur ve yeni isteklerini kabul etmek için yeni bir uygulama havuzu oluşturur. Bir iş akışı bir yanıt gönderdikten sonra çalışmaya devam ederse, IIS 7.0 yapılmakta olan çalışmanın uyumlu olmaz ve barındırma uygulama havuzunu geri dönüştür. Böyle, iş akışını iptal edilecek ve izleme hizmetleri kayıt bir [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md) neden boş alan iletisi.  
>   
>  Kalıcılık kullandıysanız, konak açıkça iptal edilmiş örneklerden son Kalıcılık noktası yeniden başlatmanız gerekir.  
>   
>  AppFabric kullandıysanız, Kalıcılık kullanılıyorsa, iş akışı yönetimi hizmetinin sonunda son başarılı Kalıcılık noktasından iş akışı devam edecek. İş akışı iptal ettiğinde hiçbir Kalıcılık kullanılır ve iş akışı bir istek/yanıt deseni dışındaki işlemleri gerçekleştirir, veriler kaybolacak.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Bir iş akışı özel bir Windows hizmetinde barındırma  
 İş akışı barındırmak için bir özel iş akışı hizmeti oluşturma çok sayıda kullanıma hazır AppFabric tarafından sağlanan işlevselliği çoğaltmak Geliştirici gerektirir, ancak daha fazla esneklik için özel işlevsellikle izin verir. AppFabric bir seçenek olmadığı durumlarda, bu seçenek yalnızca kabul edilmelidir.

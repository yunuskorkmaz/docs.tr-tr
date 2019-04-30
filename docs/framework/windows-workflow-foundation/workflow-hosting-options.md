---
title: İş Akışı Barındırma Seçenekleri
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 2a03c7b5e15b76eabc714f44624f04d3385720d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670225"
---
# <a name="workflow-hosting-options"></a>İş Akışı Barındırma Seçenekleri
Bir konsol uygulamasında barındırılan iş akışı Windows Workflow Foundation (WF) örnekleri çoğu kullanın, ancak bu gerçek iş akışları için gerçekçi bir senaryo değildir. Gerçek iş uygulamalarını iş akışlarında barındırılacak kalıcı işlemleri bir Windows hizmeti yazılan geliştirici veya bir sunucu uygulaması gibi- [!INCLUDE[iisver](../../../includes/iisver-md.md)] veya AppFabric. Bu yaklaşımların arasındaki farklar aşağıdaki gibidir.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>IIS Windows AppFabric ile iş akışları barındırma  
 AppFabric ile IIS kullanarak iş akışları için tercih edilen ana bilgisayardır. IIS üzerinde tek başına HTTP üzerindeki bağımlılığı kaldırır Windows Etkinleştirme hizmeti AppFabric kullanarak iş akışları için ana bilgisayar uygulamasıdır.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Tek başına bir IIS iş akışları barındırma  
 Kullanarak [!INCLUDE[iisver](../../../includes/iisver-md.md)] yönetim ve izleme çalışan uygulamaların Bakımı kolaylaştıran AppFabric ile kullanılabilen araçları olduğundan tek başına önerilmez. İş akışları alanınızın yalnızca barındırılması [!INCLUDE[iisver](../../../includes/iisver-md.md)] AppFabric için taşıma ile altyapıyla ilgili endişelerini yoksa tek başına.  
  
> [!WARNING]
>  [!INCLUDE[iisver](../../../includes/iisver-md.md)] Uygulama havuzları, çeşitli nedenlerle düzenli aralıklarla geri dönüştürür. Bir uygulama havuzu geri dönüştürüldüğünde, IIS eski havuzuna iletileri kabul etmeye durdurur ve yeni isteklerini kabul etmek için yeni bir uygulama havuzu oluşturur. Bir iş akışı bir yanıt gönderdikten sonra çalışmaya devam ederse [!INCLUDE[iisver](../../../includes/iisver-md.md)] yapılmakta olan çalışmanın uyumlu olmaz ve barındırma uygulama havuzunu geri dönüştür. Böyle, iş akışını iptal edilecek ve izleme hizmetleri kayıt bir [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md) neden boş alan iletisi.  
>   
>  Kalıcılık kullandıysanız, konak açıkça iptal edilmiş örneklerden son Kalıcılık noktası yeniden başlatmanız gerekir.  
>   
>  AppFabric kullandıysanız, Kalıcılık kullanılıyorsa, iş akışı yönetimi hizmetinin sonunda son başarılı Kalıcılık noktasından iş akışı devam edecek. İş akışı iptal ettiğinde hiçbir Kalıcılık kullanılır ve iş akışı bir istek/yanıt deseni dışındaki işlemleri gerçekleştirir, veriler kaybolacak.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Bir iş akışı özel bir Windows hizmetinde barındırma  
 İş akışı barındırmak için bir özel iş akışı hizmeti oluşturma çok sayıda kullanıma hazır AppFabric tarafından sağlanan işlevselliği çoğaltmak Geliştirici gerektirir, ancak daha fazla esneklik için özel işlevsellikle izin verir. AppFabric bir seçenek olmadığı durumlarda, bu seçenek yalnızca kabul edilmelidir.

---
title: İş Akışı Barındırma Seçenekleri
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 4eaed147f312f3963aa1ca1d4f5dbe010c4189ad
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037830"
---
# <a name="workflow-hosting-options"></a>İş Akışı Barındırma Seçenekleri
Windows Workflow Foundation (WF) örneklerinin çoğu, bir konsol uygulamasında barındırılan iş akışlarını kullanır, ancak bu gerçek dünyada iş akışları için gerçekçi bir senaryodur. Gerçek iş uygulamalarındaki iş akışları kalıcı işlemlerde (geliştirici tarafından yazılan bir Windows hizmeti veya IIS 7,0 veya AppFabric gibi bir sunucu uygulaması) barındırılacak. Bu yaklaşımlar arasındaki farklılıklar aşağıda verilmiştir.

## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Windows AppFabric ile IIS 'de iş akışlarını barındırma

IIS 'yi AppFabric ile kullanmak, iş akışları için tercih edilen ana bilgisayar. AppFabric kullanan iş akışları için konak uygulaması, Windows etkinleştirme hizmeti 'dir ve bu, HTTP üzerinden IIS üzerinden bağımlılığı ortadan kaldırır.

## <a name="hosting-workflows-in-iis-alone"></a>Yalnızca IIS 'de iş akışlarını barındırma

Çalışan uygulamaların bakımını kolaylaştıran AppFabric ile kullanılabilen yönetim ve izleme araçları olduğundan tek başına IIS 7,0 kullanılması önerilmez. İş akışları yalnızca, AppFabric 'e geçiş ile ilgili altyapı sorunları varsa yalnızca IIS 7,0 ' de barındırılmalıdır.

> [!WARNING]
> IIS 7,0, çeşitli nedenlerle uygulama havuzlarını düzenli aralıklarla geri dönüştürür. Bir uygulama havuzu geri dönüştürüldüğünde, IIS eski havuza ileti kabul etmeyi durduruyor ve yeni istekleri kabul etmek için yeni bir uygulama havuzu başlatır. Bir iş akışı yanıt gönderdikten sonra çalışmaya devam ederse, IIS 7,0 gerçekleştirilen çalışmanın farkında olmaz ve barındırma uygulama havuzunu geri dönüştürebilir. Bu durumda, iş akışı iptal edilir ve izleme hizmetleri boş bir neden alanıyla [1004-Workflowınstancedurdurulan](1004-workflowinstanceaborted.md) bir ileti kaydeder.
>
> Kalıcılık kullanılırsa, konağın durdurulan örnekleri son Kalıcılık noktasından açıkça yeniden başlatması gerekir.
>
> AppFabric kullanılıyorsa, iş akışı yönetim hizmeti, kalıcılık kullanılırsa son başarılı Kalıcılık noktasından iş akışını sürdürür. Kalıcılık kullanılmazsa ve iş akışı bir Istek/yanıt deseninin dışında işlemler gerçekleştirdiğinde, iş akışı iptal edildiğinde veriler kaybedilir.

## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Özel bir Windows hizmetinde iş akışını barındırma

İş akışını barındırmak için özel bir iş akışı hizmeti oluşturmak, geliştiricinin, AppFabric tarafından kullanıma hazır olarak sunulan işlevlerin çoğunu çoğaltmasını gerektirir, ancak özel işlevlerle daha fazla esneklik sağlar. Bu seçenek yalnızca, AppFabric bir seçenek olmadığı durumlarda dikkate alınmalıdır.

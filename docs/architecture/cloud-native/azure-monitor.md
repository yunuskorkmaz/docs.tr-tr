---
title: Azure İzleyici
description: Sisteminizde görünürlük kazanmak için Azure Monitor'u kullanmak çalışıyor.
ms.date: 02/05/2020
ms.openlocfilehash: 4e5ddba6c1c13dc65662a7748d4ae3a58a6a6f68
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805622"
---
# <a name="azure-monitor"></a>Azure İzleyici

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Başka hiçbir bulut sağlayıcısı, Azure'da bulunan bulut uygulaması izleme çözümünden bu kadar olgun değildir. Azure Monitor, sisteminizin durumuna görünürlük, herhangi bir sorunla ilgili öngörüler ve uygulamanızın optimizasyonu sağlamak üzere tasarlanmış bir araç koleksiyonunun şemsiye adıdır.

![Azure Monitor, bulut tası uygulamasının nasıl işlediğine ilişkin bilgi sağlamak için araçlara bir koleksiyondur. ](./media/azure-monitor.png)
 **Şekil 7-12**. Azure Monitor, bulut tası uygulamasının nasıl işlediğine ilişkin bilgi sağlamak için araçlara bir koleksiyondur.

## <a name="gathering-logs-and-metrics"></a>Günlükleri ve ölçümleri toplama

Herhangi bir izleme çözümünde ilk adım mümkün olduğunca çok veri toplamaktır. Ne kadar çok veri toplanabilirse, elde edilebilen içgörüler o kadar derin olur. Enstrümanting sistemleri geleneksel olarak zor olmuştur. Basit Ağ Yönetimi Protokolü (SNMP) makine düzeyinde bilgi toplamak için altın standart protokol oldu ama bilgi ve yapılandırma büyük bir gerekli. Neyse ki, en yaygın ölçümler Azure Monitor tarafından otomatik olarak toplandığı için bu zor çalışmanın çoğu ortadan kaldırıldı.

Uygulama düzeyi ölçümleri ve olayları, dağıtılan uygulamaya özgü olduğundan otomatik olarak aygıt alabilmeleri mümkün değildir. Bu ölçümleri toplamak için, müşteri bir siparişi kaydettiğinde veya tamamladığında olduğu gibi bu tür bilgileri doğrudan bildirmek için [SDK'lar ve API'ler kullanılabilir.](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) Özel durumlar, Application Insights aracılığıyla yakalanabilir ve Azure Monitor'a geri bildirilebilir. SDK'lar, Go, Python, JavaScript ve .NET dilleri de dahil olmak üzere Bulut Yerel Uygulamalarında bulunan tüm dilleri destekler.

Uygulamanızın durumu hakkında bilgi toplamanın nihai amacı, son kullanıcılarınızın iyi bir deneyim yaşamasını sağlamaktır. Kullanıcıların [web](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)dışında test yapmaktan daha sorunlar yaşıyorsanız söylemek için daha iyi bir yol var mı? Bu testler, web sitenizi dünyanın dört bir yanındaki yerlerden pinglekaydetmek kadar basit olabilir veya aracıların siteye giriş yapıp kullanıcı eylemlerini simüle etme leri kadar basit olabilir.

## <a name="reporting-data"></a>Verileri raporlama

Veriler toplandıktan sonra, değiştirilebilir, özetlenebilir ve grafiklere çizilebilir, bu da kullanıcıların sorun olduğunda anında görmelerini sağlar. Bu grafikler panolarda veya sistemin bazı yönleri hakkında bir hikaye anlatmak üzere tasarlanmış çok sayfalı bir rapor olan Workbook'larda toplanabilir.

Hiçbir modern uygulama bazı yapay zeka veya makine öğrenme olmadan tam olacaktır. Bu amaçla, aksi takdirde gizlenecek eğilimleri ve bilgileri ayıklamanızı sağlamak için veriler Azure'daki çeşitli makine öğrenimi araçlarına [aktarılabilir.](https://www.youtube.com/watch?v=Cuza-I1g9tw)

Application Insights, kayıtları bulmak, özetlemek ve hatta grafikleri çizmek için kullanılabilecek Kusto adında güçlü bir sorgu dili sağlar. Örneğin, bu sorgu Kasım 2007 ayına ait tüm kayıtları bulur, duruma göre gruplanır ve ilk 10'u pasta grafiği olarak çizer.

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

![Uygulama Öngörüleri Sorgu](./media/azure-monitor.png)
Şekli Şekil**7-13'ün**sonucu. Uygulama Öngörüleri Sorgusunun sonucu.

Bir ya da iki saat geçirmek için harika bir yer dir [Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) sorguları ile deneme için bir oyun alanı vardır. [Örnek sorguları](https://docs.microsoft.com/azure/kusto/query/samples) okumak da öğretici olabilir.

## <a name="dashboards"></a>Panolar

Azure Monitor'daki bilgileri yüzeye çıkarmak için kullanılabilecek birkaç farklı pano teknolojisi vardır. Belki de en basiti, Uygulama İstatistikleri'ndeki sorguları çalıştırmak ve [verileri bir grafiğe çizmektir.](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)

![Ana Azure Pano](./media/azure-monitor.png)
Şekil**7-14'te**gömülü Uygulama Öngörüleri grafiklerine bir örnek . Ana Azure Panosuna katışılmış Uygulama Öngörüleri grafiklerinin bir örneği.

Bu grafikler daha sonra pano özelliğini kullanarak Azure portalına uygun şekilde katıştılabilir. Azure Monitor verileri, birden fazla veri katmanına girebilme gibi daha titiz gereksinimleri olan kullanıcılar için [Power BI'de](https://powerbi.microsoft.com/)kullanılabilir. Power BI, birçok farklı veri kaynağından veri tolayabilen, sektör lideri, kurumsal sınıf, iş zekası aracıdır.

![Bir örnek Güç](./media/azure-monitor.png)
BI pano**Şekil 7-15**. Örnek bir Güç BI panosu.

## <a name="alerts"></a>Uyarılar

Bazen, veri panoları na sahip olmak yetersizdir. Kimse panoları izlemek için uyanık ise, o zaman hala bir sorun ele önce saatlerce olabilir, hatta tespit. Bu amaçla, Azure Monitor aynı zamanda bir üst çentik [uyarı çözümü](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview)de sağlar. Uyarılar, şu lar dahil olmak üzere çok çeşitli koşullar tarafından tetiklenebilir:

- Ölçüm değerleri
- Günlük arama sorguları
- Etkinlik Günlüğü etkinlikleri
- Temel alınan Azure platformunun durumu
- Web sitesi kullanılabilirliği için testler

Tetiklendiğinde, uyarılar çok çeşitli görevleri gerçekleştirebilir. Basit tarafta, uyarılar yalnızca bir e-posta listesine e-posta bildirimi veya bir kişiye kısa mesaj gönderebilir. Daha fazla ilgili uyarılar, belirli bir uygulama için kimin nöbette olduğunu bilen PagerDuty gibi bir araçta iş akışını tetikleyebilir. Uyarılar, [Microsoft Flow'da](https://flow.microsoft.com/) iş akışları için sınırsız olanaklara yakın bir şekilde kilit açma eylemlerini tetikleyebilir.

Uyarıların yaygın nedenleri belirlendikçe, uyarılar uyarıların yaygın nedenleri ve bunları gidermek için atılacak adımlar la ilgili ayrıntılarla geliştirilebilir. Son derece olgun bulut tabanlı uygulama dağıtımları, bir ölçek kümesinden başarısız düğümleri kaldırma veya otomatik ölçeklendirme etkinliğini tetikleme gibi eylemleri gerçekleştiren kendi kendine iyileştirici görevleri başlatmayı seçebilir. Sonunda artık bir canlı site sorunu çözmek için saat 2'de on-call personel uyanmak için gerekli olabilir sistem telafi etmek için kendini ayarlamak mümkün olacak ya da en azından birisi ertesi sabah işe gelene kadar boyunca gevşek.

Azure Monitor, dağıtılan uygulamaların normal çalışma parametrelerini anlamak için makine öğreniminden otomatik olarak yararlanır. Bu, normal parametrelerinin dışında çalışan hizmetleri algılamasını sağlar. Örneğin, sitedeki tipik hafta içi trafiği dakikada 10.000 istek olabilir. Ve sonra, belirli bir haftada, aniden istek sayısı dakikada çok sıra dışı 20.000 istek vurur. [Akıllı Algılama,](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) normdaki bu sapmayı fark edecek ve bir uyarı tetikleyecek. Aynı zamanda, trend analizi, trafik yükü beklendiği zaman yanlış pozitif leri ateşlemekten kaçınacak kadar akıllıdır.

## <a name="references"></a>Başvurular

- [Azure İzleyici](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Önceki](monitoring-azure-kubernetes.md)
>[Sonraki](identity.md)

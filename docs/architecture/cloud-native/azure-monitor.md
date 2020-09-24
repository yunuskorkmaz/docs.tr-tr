---
title: Azure İzleyici
description: Sisteminizin üzerinde görünürlük elde etmek için Azure Izleyici 'yi kullanma.
ms.date: 07/05/2020
ms.openlocfilehash: 65e17740dba49c3ac3f6e13462897b5342da6710
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160976"
---
# <a name="azure-monitor"></a>Azure İzleyici

Başka bir bulut sağlayıcısı, Azure 'da bulunan bir bulut uygulaması izleme çözümünün bir üyesi değildir. Azure Izleyici, sisteminizin durumuna ilişkin görünürlük sağlamak için tasarlanan bir araç koleksiyonu için şemsiye bir addır. Bulut Yerel hizmetlerinizin nasıl çalıştığını anlamanıza yardımcı olur ve bunları etkileyen sorunları önceden belirler. Şekil 7-12, Azure Izleyici 'nin yüksek düzeyde bir görünümünü sunar.

![Azure Izleyici 'nin üst düzey görünümü. ](./media/azure-monitor.png)
 **Şekil 7-12**. Azure Izleyici 'nin üst düzey görünümü.

## <a name="gathering-logs-and-metrics"></a>Günlükleri ve ölçümleri toplama

Herhangi bir izleme çözümünde ilk adım mümkün olduğunca çok veri toplamaktır. Daha fazla veri toplandıktan sonra Öngörüler daha derin. Aletsiz sistemler, geleneksel olarak güçleşir. Basit Ağ Yönetim Protokolü (SNMP), makine düzeyinde bilgi toplamak için kullanılan altın standart protokoldür, ancak bilgi ve yapılandırma için harika bir işlem gerektirdi. Neyse ki, en yaygın ölçümler Azure Izleyici tarafından otomatik olarak toplandığından, bu sabit çalışmanın çoğu ortadan kaldırılmıştır.

Dağıtılan uygulamaya özgü olduklarından, uygulama düzeyi ölçümleri ve olayları otomatik olarak işaretleme yapılamaz. Bu ölçümleri toplamak için, bir müşterinin bir siparişi kaydolduğunda veya tamamladığı durumlarda olduğu gibi, bu bilgileri doğrudan raporlamak için [kullanılabilir SDK 'lar ve API 'ler](/azure/azure-monitor/app/api-custom-events-metrics) vardır. Ayrıca, özel durumlar Application Insights aracılığıyla Azure Izleyici 'ye geri yakalanıp rapor edilebilir. SDK 'lar, Go, Python, JavaScript ve .NET dillerini de içeren bulut Yerel uygulamalarında bulunan her dilin çoğunu destekler.

Uygulamanızın durumu hakkında bilgi toplamanın nihai hedefi, son kullanıcılarınızın iyi bir deneyim aldığından emin olmaktır. Kullanıcıların, [dışarıdaki Web testlerini](/azure/azure-monitor/app/monitor-web-app-availability)yapmaktan sorun yaşadığını söylemek için daha iyi bir yol var mı? Bu testler, dünyanın dört bir yanındaki konumlardan veya aracılardan biri sitede oturum açıp Kullanıcı eylemlerinin benzetimini yaparak Web sitenizde ping hale kadar basit olabilir.

## <a name="reporting-data"></a>Raporlama verileri

Veriler toplandıktan sonra, kullanıcıların sorun olduğunda anında görmesine izin veren grafikler üzerinde değiştirilebilir, özetlenir ve çizilebilirler. Bu grafikler, sistemin bazı yönlerini anlatmak üzere tasarlanan çok sayfalı bir rapor olan panolar veya çalışma kitaplarında toplanabilir.

Yapay zeka veya Machine Learning olmadan modern uygulama tamamlanmaz. Bu uçta, veriler başka bir şekilde gizlenebileceği eğilimleri ve bilgileri ayıklamanızı sağlamak için Azure 'daki çeşitli makine öğrenimi araçlarına veri [geçirilebilir](https://www.youtube.com/watch?v=Cuza-I1g9tw) .

Application Insights, kayıtları sorgulayabilir, özetleyebilir ve hatta grafik *ÇizKusto* adlı güçlü (SQL benzeri) bir sorgu dili sağlar. Örneğin, aşağıdaki sorgu, 2007 Kasım ayının tüm kayıtlarını bulur, bunları durumlarına göre gruplayın ve bir pasta grafiği olarak ilk 10 ' u çizmez.

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

Şekil 7-13 bu Application Insights sorgusunun sonuçlarını gösterir.

![Sorgu sonuçları ](./media/application_insights_example.png)
 **şekil 7-13**Application Insights. Sorgu sonuçlarını Application Insights.

[Kusto sorgularını denemek için bir oyun](https://dataexplorer.azure.com/clusters/help/databases/Samples) vardır. [Örnek sorguları](/azure/kusto/query/samples) okuma da çalıştırılabilir.

## <a name="dashboards"></a>Panolar

Azure Izleyici 'den bilgileri yüzeye almak için kullanılabilecek çeşitli farklı Pano teknolojileri vardır. Belki de en basit, Application Insights sorguları çalıştırmak ve [verileri bir grafiğe çizmeniz](/azure/azure-monitor/learn/tutorial-app-dashboards)olabilir.

![Ana Azure panosu ](./media/azure_dashboard.png)
 **Şekil 7-14**' de gömülü Application Insights grafiklerin bir örneği. Ana Azure panosuna katıştırılmış Application Insights grafik örneği.

Bu grafikler daha sonra Pano özelliğinin kullanımıyla Azure portal uygun şekilde gömülebilir. Çeşitli veri katmanlarında ayrıntıya gidebilmek gibi daha fazla exacting gereksinimi olan kullanıcılar için Azure Izleyici verileri [Power BI](https://powerbi.microsoft.com/)kullanılabilir. Power BI, birçok farklı veri kaynağından veri toplayabilen sektör lideri, kurumsal sınıf, iş zekası aracıdır.

![Örnek Power BI panosu](./media/powerbidashboard.png)

**Şekil 7-15**. Pano Power BI bir örnek.

## <a name="alerts"></a>Uyarılar

Bazen veri panoları yeterli değildir. Panoları izlemek için kimse uyanık yoksa, bir sorun giderilebilmesi veya hatta algılanmadan önce bu süre çok saat kadar sürebilir. Azure Izleyici, bu uçta bir üst düzey [Uyarı çözümü](/azure/azure-monitor/platform/alerts-overview)de sağlar. Uyarılar aşağıdakiler dahil olmak üzere çok çeşitli koşullarla tetiklenebilir:

- Ölçüm değerleri
- Günlük arama sorguları
- Etkinlik günlüğü olayları
- Temel alınan Azure platformunun durumu
- Web sitesi kullanılabilirliği için testler

Tetiklendiğinde, uyarılar çok çeşitli görevler gerçekleştirebilir. Basit tarafta, uyarılar yalnızca bir posta listesine e-posta bildirimi veya bir kişiye metin iletisi gönderebilir. Daha fazla ilgili uyarı, belirli bir uygulama için kimin çağırdığının farkında olan Pagerharcı gibi bir araçta iş akışını tetikleyebiliyor. Uyarılar, iş akışları için sınırsız olasılıklardan [Microsoft Flow](https://flow.microsoft.com/) kilit açma sırasında eylemleri tetikleyebilir.

Uyarıların yaygın nedenleri tanımlandıkları için uyarılar, uyarıların genel nedenleri ve bunları çözmek için gereken adımlar hakkında ayrıntılarla iyileştirilen şekilde geliştirilebilir. Yüksek derecede çok büyük ölçekli bulut Yerel uygulama dağıtımları, hatalı düğümleri bir ölçek kümesinden kaldırma veya otomatik ölçeklendirme etkinliğini tetikleme gibi eylemleri gerçekleştiren kendi kendini onaran görevleri başlatabilir. Son olarak, sistem kendisini bir sonraki sabah işe ulaşana kadar bir süre önce veya en az bir şekilde ayarlayacağından, bir canlı site sorununu çözmek için, daha önce 2.

Azure Izleyici, dağıtılan uygulamaların normal işletim parametrelerini anlamak için makine öğrenimini otomatik olarak kullanır. Bu, BT 'nin normal parametrelerinin dışında çalışan hizmetleri algılamasını sağlar. Örneğin, sitedeki tipik iş günü trafiği dakikada 10.000 istek olabilir. Daha sonra, belirli bir hafta boyunca istek sayısı, dakikada yüksek olağandışı 20.000 istek üzerine gelir. [Akıllı algılama](/azure/azure-monitor/app/proactive-diagnostics) , norm karşı bu sapmayı fark eder ve bir uyarı tetikler. Aynı zamanda, trafik yükü beklendiğinde hatalı pozitif sonuçlar tetiklemeden kaçınmak için eğilim analizi yeterince akıllı olur.

## <a name="references"></a>Başvurular

- [Azure İzleyici](/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Önceki](monitoring-azure-kubernetes.md) 
> [Sonraki](identity.md)

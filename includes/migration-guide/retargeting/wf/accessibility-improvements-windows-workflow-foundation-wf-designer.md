---
ms.openlocfilehash: d420be76645fc71ac922542fa49f799a473e9a83
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614856"
---
### <a name="accessibility-improvements-in-windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) iş akışı tasarımcısında erişilebilirlik geliştirmeleri

#### <a name="details"></a>Ayrıntılar

Windows Workflow Foundation (WF) iş akışı Tasarımcısı, erişilebilirlik teknolojileriyle nasıl çalıştığını geliştirir. Bu geliştirmeler aşağıdaki değişiklikleri içerir:

- Sekme sırası, bazı denetimlerde soldan sağa ve yukarıdan aşağıya doğru olarak değişir:
- Etkinlik için bağıntı verilerini ayarlamaya yönelik bağıntı Başlat penceresi <xref:System.ServiceModel.Activities.InitializeCorrelation>
- <xref:System.ServiceModel.Activities.Receive>,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> Ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikleri için içerik tanımı penceresi
- Klavye aracılığıyla daha fazla işlev mevcuttur:
- Bir etkinliğin özelliklerini düzenlediğinizde, özellik grupları ilk odaklandığında klavye tarafından daraltılabilirler.
- Uyarı simgeleri artık klavye tarafından erişilebilir.
- Özellikler penceresi daha fazla özellik düğmesine artık klavye tarafından erişilebilir.
- Klavye kullanıcıları artık İş Akışı Tasarımcısı bağımsız değişkenler ve değişkenler bölmelerinde üst bilgi öğelerine erişebilir.
- Odaklanılmış öğelerin şu durumlarda geliştirilmiş görünürlüğü:
- İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri kılavuzlarına satır ekleme.
- <xref:System.ServiceModel.Activities.ReceiveReply>Ve etkinliklerindeki alanlar arasında sekme <xref:System.ServiceModel.Activities.SendReply> .
- Değişkenler veya bağımsız değişkenler için varsayılan değerleri ayarlama
- Ekran okuyucular artık doğru şekilde tanıyabilir:
- İş akışı tasarımcısında ayarlanan kesme noktaları.
- <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> Ve <xref:System.ServiceModel.Activities.CorrelationScope> etkinlikleri.
- <xref:System.ServiceModel.Activities.Receive>Etkinliğin içeriği.
- Etkinliğin hedef türü <xref:System.Activities.Statements.InvokeMethod> .
- Etkinliğin özel durum ComboBox 'ı ve finally bölümü <xref:System.Activities.Statements.TryCatch> .
- İleti türü açılan kutusu, bağıntı başlatıcıları Ekle penceresinde, içerik tanımı penceresinde ve CorrelatesOn Defintion penceresinde, ileti etkinliklerinin ( <xref:System.ServiceModel.Activities.Receive> ,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> ve) yer aldığı ayırıcı <xref:System.ServiceModel.Activities.ReceiveReply> .
- Durum makinesi geçişleri ve geçiş hedefleri.
- Etkinlikler üzerinde ek açıklamalar ve bağlayıcılar <xref:System.Activities.Statements.FlowDecision> .
- Etkinlikler için bağlam (sağ tıklama) menüleri.
- Özellik değeri düzenleyicileri, aramayı temizle düğmesi, kategoriye ve alfabetik sıralama düğmelerine göre ve Özellikler kılavuzundaki Ifade Düzenleyicisi iletişim kutusu.
- İş Akışı Tasarımcısı yakınlaştırma yüzdesi.
- <xref:System.Activities.Statements.Parallel>Ve <xref:System.Activities.Statements.Pick> etkinliklerindeki ayırıcı.
- <xref:System.Activities.Statements.InvokeDelegate>Etkinlik.
- Sözlük Etkinlikleri ( `Microsoft.Activities.AddToDictionary&lt;TKey,TValue>` , `Microsoft.Activities.RemoveFromDictionary&lt;TKey,TValue>` , vb.) Için türleri seçin penceresi.
- .NET tür araştır ve Seç penceresi.
- İş Akışı Tasarımcısı içerik haritaları.
- Yüksek Karşıtlık Temaları seçen kullanıcılar, İş Akışı Tasarımcısı görünürlüğünde birçok geliştirme ve öğeler arasında daha fazla karşıtlık oranı ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi denetimler görür.

#### <a name="suggestion"></a>Öneri

Yeniden barındırılan bir iş akışı tasarlayıcı içeren bir uygulamanız varsa, uygulamanız bu eylemlerden birini gerçekleştirerek bu değişikliklerden faydalanabilir:

- .NET Framework 4.7.1 hedeflemek için uygulamanızı yeniden derleyin. Bu erişilebilirlik değişiklikleri varsayılan olarak etkindir.
- Uygulamanız .NET Framework 4,7 veya önceki bir sürümü hedefliyorsa ancak .NET Framework 4.7.1 üzerinde çalışıyorsa, aşağıdaki örnekte gösterildiği gibi, aşağıdaki [AppContext anahtarını](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` app.config dosyanın bölümüne ekleyerek ve olarak ayarlarsanız, bu eski erişilebilirlik davranışlarını devre dışı bırakabilirsiniz `false` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

.NET Framework 4.7.1 veya üstünü hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |

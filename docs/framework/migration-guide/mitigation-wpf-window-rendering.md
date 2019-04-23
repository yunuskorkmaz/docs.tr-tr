---
title: 'Azaltma: WPF penceresi işleme'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afad3c3bf6c950b4ffe4e8bed2ff86a416a31a87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978815"
---
# <a name="mitigation-wpf-window-rendering"></a>Azaltma: WPF penceresi işleme

İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] tek görünen bir çoklu monitör senaryosunda dışında genişletir, Windows 8'de çalıştırma ve üzeri, pencerenin tamamını kırpma olmadan oluşturulur.

## <a name="impact"></a>Etki

Genel olarak, bir pencerenin tamamını kırpma olmadan birden çok monitör genelinde işleme beklenen bir davranıştır. Ancak, Windows 7 ve önceki sürümleri, önemli performans etkisi pencereyi ikinci monitörde bir kısmını işlemeye sahip olduğu tek bir görüntü genişlettiğinizde, WPF windows kırpılır.

Büyük bir dizi faktöre bağlı olduğundan işleme WPF windows, Windows 8 ve üzeri izleyiciler arasında kesin etkisini tam olarak ölçülebilir değil. Bazı durumlarda, performans, özellikle izleyiciler payından windows grafik kullanımı yoğun uygulamalar çalıştırmak ve kullanıcılar için istenmeyen bir etkisi hala üretebilir. Diğer durumlarda, .NET Framework sürümleri arasında tutarlı bir davranış yalnızca isteyebilirsiniz.

## <a name="mitigation"></a>Azaltma

Bu değişiklik devre dışı bırakabilir ve tek bir görüntü genişletir, bir WPF penceresi kırpma, önceki davranışı geri döndür. Bunu yapmak için iki yol vardır:

- Ekleyerek `<EnableMultiMonitorDisplayClipping>` öğesine `<appSettings>` bölümü, uygulama yapılandırma dosyasını, devre dışı bırakın veya Windows 8 veya üzeri çalıştıran uygulamalarda bu davranışı etkinleştirin. Örneğin, aşağıdaki yapılandırma bölümüne kırpma olmadan işleme devre dışı bırakır:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  `<EnableMultiMonitorDisplayClipping>` Yapılandırma ayarı, iki değerden birini içerebilir:

  - `true`, kırpma sınırları işleme sırasında izlemek için Windows etkinleştirmek için.

  - `false`, işleme sırasında sınırları izlemek için Windows kırpmayı devre dışı bırakmak için.

- Ayarlayarak <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> özelliğini `true` uygulamanın başlangıcında.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)

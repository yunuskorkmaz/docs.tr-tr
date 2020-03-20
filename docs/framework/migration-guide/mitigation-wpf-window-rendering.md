---
title: 'Azaltma: WPF Penceresi İşleme'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: 42d6abf1ba6ed7c17a5a5604e98b5ee46d0c3ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457772"
---
# <a name="mitigation-wpf-window-rendering"></a>Azaltma: WPF Penceresi İşleme

Windows 8 ve üzeri üzerinde çalışan .NET Framework 4.6'da, çoklu monitör senaryosunda tek ekranın dışına uzandığında tüm pencere kırpma olmadan işlenir.

## <a name="impact"></a>Etki

Genel olarak, tüm pencereyi kırpmadan birden çok monitör arasında işlemek beklenen davranıştır. Ancak, Windows 7 ve önceki sürümlerde, pencerenin bir bölümünün ikinci monitörde işlenmesi önemli bir performans etkisi olduğundan, tek bir ekranın ötesine geçtiklerinde WPF pencereler kırpılır.

WPF pencerelerini Windows 8 ve üzeri monitörler arasında oluşturmanın kesin etkisi, çok sayıda etkene bağlı olduğundan tam olarak ölçülemez. Bazı durumlarda, özellikle grafik yoğun uygulamaları çalıştıran ve windows straddling monitörleri olan kullanıcılar için performans üzerinde istenmeyen bir etki yaratabilir. Diğer durumlarda, .NET Framework sürümlerinde tutarlı bir davranış isteyebilirsiniz.

## <a name="mitigation"></a>Risk azaltma

Bu değişikliği devre dışı bırakıp, tek bir ekranın ötesine uzandığında WPF penceresini kırpma önceki davranışına geri dönebilirsiniz. Bunu yapmak için iki yol vardır:

- `<EnableMultiMonitorDisplayClipping>` Uygulama yapılandırma dosyanızın `<appSettings>` bölümüne öğeyi ekleyerek, Windows 8 veya sonraki uygulamalarda bu davranışı devre dışı layabilir veya etkinleştirebilirsiniz. Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işleme devre dışı katıyor:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  Yapılandırma `<EnableMultiMonitorDisplayClipping>` ayarı iki değerden biri olabilir:

  - `true`, işleme sırasında sınırları izlemek için pencerelerin kırpma etkinleştirmek için.

  - `false`, işleme sırasında sınırları izlemek için pencerelerin kırpma devre dışı.

- <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> Uygulama başlangıç `true` noktasında özelliği ayarlayarak.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)

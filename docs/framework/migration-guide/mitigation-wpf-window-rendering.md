---
title: 'Azaltma: WPF Penceresi İşleme'
description: Windows 8 veya üzeri sürümlerde çalışan .NET Framework 4,6 ' de WPF pencere işleme etkisi ve hafifletme hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: d624478d17a4076107438f71b0a86eeb6d9f3ea4
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475339"
---
# <a name="mitigation-wpf-window-rendering"></a>Azaltma: WPF Penceresi İşleme

Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,6 ' de, tüm pencere, birden çok izleyici senaryosunda tek bir görüntü dışına genişlemediğinde kırpma olmadan işlenir.

## <a name="impact"></a>Etki

Genel olarak, bir pencerenin tamamını kırpmadan birden çok monitörde işlemek beklenen davranıştır. Bununla birlikte, Windows 7 ve önceki sürümlerde WPF pencereleri, ikinci monitörde pencerenin bir kısmını işlemek önemli bir performans etkisi sağladığından, tek bir ekranı genişlediklerinde kırpılır.

WPF pencerelerini Windows 8 ve üzeri sürümlerde izlemenin kesin etkileri, çok sayıda etkene bağlı olduğundan tam olarak nicelik yapamaz. Bazı durumlarda, özellikle grafik yoğun uygulamalar çalıştıran ve Windows tarafından ayarlanan izleyiciler bulunan kullanıcılar için performans üzerinde istenmeyen bir etkisi olabilir. Diğer durumlarda, .NET Framework sürümler arasında tutarlı bir davranış de isteyebilirsiniz.

## <a name="mitigation"></a>Risk azaltma

Bu değişikliği devre dışı bırakabilir ve tek bir görüntüleme ötesinde bir WPF penceresinin kırpılması için önceki davranışa geri dönebilir. Bunu yapmak için iki yol vardır:

- `<EnableMultiMonitorDisplayClipping>` `<appSettings>` Uygulama yapılandırma dosyanızın bölümüne öğesi eklenerek, Windows 8 veya üzeri sürümlerde çalışan uygulamalarda bu davranışı etkinleştirebilir veya devre dışı bırakabilirsiniz. Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işlemeyi devre dışı bırakır:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  `<EnableMultiMonitorDisplayClipping>`Yapılandırma ayarı iki değerden birini içerebilir:

  - `true`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını etkinleştirmek için.

  - `false`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını devre dışı bırakmak için.

- <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A>Uygulama başlangıcında özelliğini olarak ayarlayarak `true` .

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)

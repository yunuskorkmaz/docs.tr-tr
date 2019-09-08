---
title: Mayı WPF Pencere Işleme
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13091c06561da24d2fc03f810fd8b8687b21d9a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789794"
---
# <a name="mitigation-wpf-window-rendering"></a>Mayı WPF Pencere Işleme

Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,6 ' de, tüm pencere, birden çok izleyici senaryosunda tek bir görüntü dışına genişlemediğinde kırpma olmadan işlenir.

## <a name="impact"></a>Etki

Genel olarak, bir pencerenin tamamını kırpmadan birden çok monitörde işlemek beklenen davranıştır. Bununla birlikte, Windows 7 ve önceki sürümlerde WPF pencereleri, ikinci monitörde pencerenin bir kısmını işlemek önemli bir performans etkisi sağladığından, tek bir ekranı genişlediklerinde kırpılır.

WPF pencerelerini Windows 8 ve üzeri sürümlerde izlemenin kesin etkileri, çok sayıda etkene bağlı olduğundan tam olarak nicelik yapamaz. Bazı durumlarda, özellikle grafik yoğun uygulamalar çalıştıran ve Windows tarafından ayarlanan izleyiciler bulunan kullanıcılar için performans üzerinde istenmeyen bir etkisi olabilir. Diğer durumlarda, .NET Framework sürümler arasında tutarlı bir davranış de isteyebilirsiniz.

## <a name="mitigation"></a>Azaltma

Bu değişikliği devre dışı bırakabilir ve tek bir görüntüleme ötesinde bir WPF penceresinin kırpılması için önceki davranışa geri dönebilir. Bunu yapmak için iki yol vardır:

- Uygulama yapılandırma dosyanızın `<EnableMultiMonitorDisplayClipping>` `<appSettings>` bölümüne öğesi eklenerek, Windows 8 veya üzeri sürümlerde çalışan uygulamalarda bu davranışı etkinleştirebilir veya devre dışı bırakabilirsiniz. Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işlemeyi devre dışı bırakır:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  `<EnableMultiMonitorDisplayClipping>` Yapılandırma ayarı iki değerden birini içerebilir:

  - `true`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını etkinleştirmek için.

  - `false`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını devre dışı bırakmak için.

- Uygulama başlangıcında <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> özelliğini olarak `true` ayarlayarak.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](runtime-changes-in-the-net-framework-4-6.md)

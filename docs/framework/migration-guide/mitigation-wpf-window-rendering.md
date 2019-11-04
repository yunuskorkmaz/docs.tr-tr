---
title: 'Azaltma: WPF Penceresi İşleme'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: 42d6abf1ba6ed7c17a5a5604e98b5ee46d0c3ac2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457772"
---
# <a name="mitigation-wpf-window-rendering"></a>Azaltma: WPF Penceresi İşleme

Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,6 ' de, tüm pencere, birden çok izleyici senaryosunda tek bir görüntü dışına genişlemediğinde kırpma olmadan işlenir.

## <a name="impact"></a>Etki

Genel olarak, bir pencerenin tamamını kırpmadan birden çok monitörde işlemek beklenen davranıştır. Bununla birlikte, Windows 7 ve önceki sürümlerde WPF pencereleri, ikinci monitörde pencerenin bir kısmını işlemek önemli bir performans etkisi sağladığından, tek bir ekranı genişlediklerinde kırpılır.

WPF pencerelerini Windows 8 ve üzeri sürümlerde izlemenin kesin etkileri, çok sayıda etkene bağlı olduğundan tam olarak nicelik yapamaz. Bazı durumlarda, özellikle grafik yoğun uygulamalar çalıştıran ve Windows tarafından ayarlanan izleyiciler bulunan kullanıcılar için performans üzerinde istenmeyen bir etkisi olabilir. Diğer durumlarda, .NET Framework sürümler arasında tutarlı bir davranış de isteyebilirsiniz.

## <a name="mitigation"></a>Azaltma

Bu değişikliği devre dışı bırakabilir ve tek bir görüntüleme ötesinde bir WPF penceresinin kırpılması için önceki davranışa geri dönebilir. Bunu yapmak için iki yol vardır:

- Uygulama yapılandırma dosyanızın `<appSettings>` bölümüne `<EnableMultiMonitorDisplayClipping>` öğesini ekleyerek, Windows 8 veya üzeri sürümlerde çalışan uygulamalarda bu davranışı devre dışı bırakabilir veya etkinleştirebilirsiniz. Örneğin, aşağıdaki yapılandırma bölümü kırpma olmadan işlemeyi devre dışı bırakır:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  `<EnableMultiMonitorDisplayClipping>` yapılandırma ayarı iki değerden birini içerebilir:

  - `true`, işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını etkinleştirmek için.

  - işleme sırasında sınırları izlemek üzere Windows 'un kırpılmasını devre dışı bırakmak için `false`.

- <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> özelliğini uygulama başlangıcında `true` olarak ayarlayarak.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)

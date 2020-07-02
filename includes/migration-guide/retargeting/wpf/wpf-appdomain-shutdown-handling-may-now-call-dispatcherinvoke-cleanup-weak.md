---
ms.openlocfilehash: 8b804d23247b95381f3ff83bc12c32215a420fb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614955"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a>WPF AppDomain kapatılmasını Işleme artık Dispatcher. zayıf olayların temizlenmesi sırasında Invoke çağrısı yapabilirsiniz

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.1 ve önceki sürümlerde WPF, <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> uygulama etki alanı kapatması sırasında .net Sonlandırıcı iş parçacığı üzerinde bir oluşturur.  Bu, zayıf olayların iş parçacığı durumunu algılayan şekilde temizliği yaparak .NET Framework 4.7.2 ve sonraki sürümlerde düzeltildi.  Bu nedenle, WPF <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> temizlik işlemini tamamlamaya yönelik çağrı gösterebilir. Belirli uygulamalarda, sonlandırıcısı zamanlamadaki bu değişiklik, AppDomain veya işlem kapatması sırasında özel durumlara neden olabilir.  Bu genel olarak, işlem veya AppDomain kapanmadan önce çalışan iş parçacıklarında çalışan sevkiyatcıları doğru şekilde kapatmayan uygulamalarda görülür.  Bu tür uygulamalar, sevkiyatların kullanım ömrünü doğru bir şekilde yönetebilmeleri için dikkatli olmalıdır.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.7.2 ve sonraki sürümlerde geliştiriciler, temizleme değişikliği nedeniyle ortaya çıkabilecek zamanlama sorunlarını gidermek (ancak ortadan kaldırmak) için bu sorunu devre dışı bırakabilir. Temizlemede değişikliği devre dışı bırakmak için aşağıdaki AppContext bayrağını kullanın.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |

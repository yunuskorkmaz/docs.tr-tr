---
ms.openlocfilehash: 8e75c60126abc2670053eba2c01e1fb36d1a93e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762646"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a>Zayıf olay temizleme WPF AppDomain kapatma işleme artık Dispatcher.Invoke çağırabilir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerinde, WPF olası oluşturur bir <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> AppDomain kapatma sırasında .NET Sonlandırıcı iş parçacığında.  Bu .NET Framework 4.7.2 ve sonraki sürümlerinde zayıf olayların temizleme iş parçacığı kullanan yaparak düzeltildi.  Bu nedenle, WPF çağırabilir <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> temizleme işlemini tamamlamak için. Bazı uygulamalarda, bu değişikliği zamanlama Sonlandırıcı olası AppDomain sırasında özel durumlarına neden veya kapatma işlemi.  Bu genellikle, işlem veya AppDomain kapatmadan önce çalışan iş parçacıkları üzerinde çalışan dağıtıcıları aşağı doğru kapatmayın uygulamalarda görülür.  Bu tür uygulamaların düzgün bir şekilde dağıtıcıları ömrünü yönetmek için ilgileniriz.|
|Öneri|.NET Framework 4.7.2 ve sonraki sürümlerinde, geliştiricilerin bu düzeltmenin yardımcı olmak için devre dışı bırakabilirsiniz temizleme değişikliği nedeniyle oluşabilir zamanlama sorunları hafifletmek (ancak değil ortadan). Temizleme değişiklik devre dışı bırakmak için aşağıdaki AppContext bayrağı kullanın.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|

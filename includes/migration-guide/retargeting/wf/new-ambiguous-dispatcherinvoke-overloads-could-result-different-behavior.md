---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617262"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>Yeni (belirsiz) dağıtıcı. aşırı yüklemeleri çağır farklı davranışa neden olabilir

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5, öğesine bir parametre içeren yeni aşırı yüklemeler ekler <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> <xref:System.Action> . Mevcut kod yeniden derlendiğinde, derleyiciler, Dispatcher çağrılarını çözümleyebilir. Invoke metotları için bir parametre içeren bir parametresi olan bir parametreye sahip metotları çağırır. <xref:System.Delegate> <xref:System.Action> Bir Dispatcher çağrısı olarak, bir dağıtıcı çağrısı olarak bir parametre ile aşırı yüklemeyi çağır. bir <xref:System.Delegate> parametre ile aşırı yüklemeyi çağırma <xref:System.Action> , davranış ile ilgili aşağıdaki farklılıklar oluşabilir

- Bir özel durum oluşursa, <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> ve <xref:System.Windows.Threading.Dispatcher.UnhandledException> olayları oluşturulmaz. Bunun yerine, özel durumlar olay tarafından işlenir <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> .
- , Gibi bazı üyelere yapılan çağrılar, <xref:System.Windows.Threading.DispatcherOperation.Result> işlem tamamlanana kadar engeller.

#### <a name="suggestion"></a>Öneri

Belirsizlik (ve özel durum işleme veya engelleme davranışındaki olası farklılıklar) önlemek için, Dispatcher. Invoke çağrısı, .NET Framework 4,0 yöntem aşırı yüklemesine çözümlendiğinizden emin olmak için çağırma çağrısına ikinci parametre olarak boş bir [] nesnesi geçirebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>

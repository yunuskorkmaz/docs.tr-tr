---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614750"
---
### <a name="serialport-background-thread-exceptions"></a><span data-ttu-id="c1eed-101">SerialPort arka plan iş parçacığı özel durumları</span><span class="sxs-lookup"><span data-stu-id="c1eed-101">SerialPort background thread exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="c1eed-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c1eed-102">Details</span></span>

<span data-ttu-id="c1eed-103">Akışlarla oluşturulan arka plan iş parçacıkları <xref:System.IO.Ports.SerialPort> artık işletim sistemi özel durumları oluştuğunda işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c1eed-103">Background threads created with <xref:System.IO.Ports.SerialPort> streams no longer terminate the process when OS exceptions are thrown.</span></span> <br/><span data-ttu-id="c1eed-104">.NET Framework 4,7 ve önceki sürümlerini hedefleyen uygulamalarda, bir akış ile oluşturulan arka plan iş parçacığında bir işletim sistemi özel durumu oluştuğunda bir işlem sonlandırılır <xref:System.IO.Ports.SerialPort> .</span><span class="sxs-lookup"><span data-stu-id="c1eed-104">In applications that target the .NET Framework 4.7 and earlier versions, a process is terminated when an operating system exception is thrown on a background thread created with a <xref:System.IO.Ports.SerialPort> stream.</span></span> <br/><span data-ttu-id="c1eed-105">.NET Framework 4.7.1 veya sonraki bir sürümü hedefleyen uygulamalarda, arka plan iş parçacıkları etkin seri bağlantı noktasıyla ilgili işletim sistemi olaylarını bekler ve seri bağlantı noktasının ani kaldırılması gibi bazı durumlarda kilitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c1eed-105">In applications that target the .NET Framework 4.7.1 or a later version, background threads wait for OS events related to the active serial port and could crash in some cases, such as sudden removal of the serial port.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c1eed-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="c1eed-106">Suggestion</span></span>

<span data-ttu-id="c1eed-107">.NET Framework 4.7.1 ' i hedefleyen uygulamalar için, aşağıdaki, dosyanızın bölümüne aşağıdakileri ekleyerek özel durum işlemesini devre dışı bırakabilirsiniz `<runtime>` `app.config` :</span><span class="sxs-lookup"><span data-stu-id="c1eed-107">For apps that target the .NET Framework 4.7.1, you can opt out of the exception handling if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

<span data-ttu-id="c1eed-108">.NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.7.1 veya sonraki sürümlerde çalışan uygulamalar için, dosyanızın bölümüne aşağıdakini ekleyerek özel durum işlemeye geçebilirsiniz `<runtime>` `app.config` :</span><span class="sxs-lookup"><span data-stu-id="c1eed-108">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.1 or later, you can opt in to the exception handling by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| <span data-ttu-id="c1eed-109">Name</span><span class="sxs-lookup"><span data-stu-id="c1eed-109">Name</span></span>    | <span data-ttu-id="c1eed-110">Değer</span><span class="sxs-lookup"><span data-stu-id="c1eed-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c1eed-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c1eed-111">Scope</span></span>   | <span data-ttu-id="c1eed-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="c1eed-112">Minor</span></span>       |
| <span data-ttu-id="c1eed-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c1eed-113">Version</span></span> | <span data-ttu-id="c1eed-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="c1eed-114">4.7.1</span></span>       |
| <span data-ttu-id="c1eed-115">Tür</span><span class="sxs-lookup"><span data-stu-id="c1eed-115">Type</span></span>    | <span data-ttu-id="c1eed-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="c1eed-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c1eed-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c1eed-117">Affected APIs</span></span>

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>

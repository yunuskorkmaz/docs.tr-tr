---
ms.openlocfilehash: 58dbb54d42d89b450134758072e3133ae4e6b13d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496401"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System. Threading. Tasks. Task artık nesne atıldıktan sonra ObjectDisposedException oluşturmaz

#### <a name="details"></a>Ayrıntılar

Dışındaki <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> Yöntemler, <xref:System.Threading.Tasks.Task?displayProperty=fullName> <xref:System.ObjectDisposedException?displayProperty=fullName> nesne atıldıktan sonra artık özel durum oluşturmaz. Bu değişiklik önbelleğe alınan görevlerin kullanımını destekler. Örneğin, bir yöntem yeni bir görev ayırmak yerine zaten tamamlanmış bir işlemi temsil etmek için önbelleğe alınmış bir görevi döndürebilir. Herhangi bir görev kullanıcısı bunu atabildiğinden ve bu da onu kullanışsız hale getirdiğinden, bu önceki .NET Framework sürümlerinde mümkün değildi.

#### <a name="suggestion"></a>Öneri

Görev yöntemlerinin <xref:System.ObjectDisposedException?displayProperty=fullName> , nesne atıldığı durumlarda artık oluşturamadığı farkında olun. Bir uygulama, bir görevin atılmış olduğunu bildirmek üzere bu özel duruma bağlı ise, görevin durumunu açıkça denetlemek için güncelleştirilmeleri gerekir <xref:System.Threading.Tasks.Task.Status> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

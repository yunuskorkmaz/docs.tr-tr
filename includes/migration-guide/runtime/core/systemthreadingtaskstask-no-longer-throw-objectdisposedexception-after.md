---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620592"
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

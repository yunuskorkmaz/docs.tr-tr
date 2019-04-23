---
ms.openlocfilehash: ab2907b05bff409fed9a370d5cbebbf3d1575d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981669"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task nesne bırakıldıktan sonra ObjectDisposedException artık throw

|   |   |
|---|---|
|Ayrıntılar|Dışında <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=name> yöntemleri artık throw bir <xref:System.ObjectDisposedException?displayProperty=name> nesne bırakıldıktan sonra özel durum. Bu değişiklik önbelleğe alınan görevlerin kullanımını destekler. Örneğin, bir yöntem yeni bir görev ayırmak yerine zaten tamamlanmış bir işlemi temsil etmek için önbelleğe alınmış bir görevi döndürebilir. Herhangi bir görev kullanıcısı bunu atabildiğinden ve bu da onu kullanışsız hale getirdiğinden, bu önceki .NET Framework sürümlerinde mümkün değildi.|
|Öneri|Görev yöntemleri artık oluşturabileceğini unutmayın <xref:System.ObjectDisposedException?displayProperty=name> nesne çıkarıldığından durumlarda. Bir uygulama bir görev atıldı öğrenmek için bu özel bağlı olarak, bunu açıkça görevin durumunu denetlemek için güncelleştirilmelidir kullanarak <xref:System.Threading.Tasks.Task.Status>.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

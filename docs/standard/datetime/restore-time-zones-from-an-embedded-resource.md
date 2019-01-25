---
title: 'Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71fc4e04c87dfa3b83eabb06361d1da94a512a5e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656811"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme

Bu konuda, bir kaynak dosyasında kaydedilen saat dilimlerini geri yükleme açıklanmaktadır. Bilgi ve saat dilimlerini kaydetme hakkında yönergeler için bkz. [nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Katıştırılmış bir kaynaktan bir Timezoneınfo nesnesinin serisini kaldırmak için

1. Kullanarak örneği oluşturmak saat dilimini alınacak özel bir saat dilimi değilse deneyin <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi.

2. Örneği bir <xref:System.Resources.ResourceManager> katıştırılmış kaynak dosyasını ve kaynak dosyasını içeren derlemeyi bir başvuru tam olarak nitelenmiş adını geçirerek nesne.

   Katıştırılmış kaynak dosyasının tam adı belirleyemiyorsa, kullanın [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derlemenin bildirimi incelemek için. Bir `.mresource` girdisini tanımlayan kaynak. Örnekte, kaynağın tam adıdır `SerializeTimeZoneData.SerializedTimeZones`.

   Saat dilimi örnekleme kodunu içeren aynı derlemede katıştırılmış kaynak dosyası ise çağırarak ona bir başvuru alabilirsiniz `static` (`Shared` Visual Basic'te) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi.

3. Çağrı <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodu başarısız olursa veya özel bir saat dilimi örneği varsa çağırarak serileştirilmiş saat dilimini içeren bir dize almak <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> yöntemi.

4. Saat dilimi veri çağırarak seri durumdan <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.

## <a name="example"></a>Örnek

Aşağıdaki örnek seri durumdan çıkarır bir <xref:System.TimeZoneInfo> katıştırılmış bir .NET XML kaynak dosyasında depolanan nesne.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Bu kod emin olmak için özel durum işleme gösterir bir <xref:System.TimeZoneInfo> uygulamanın gerektirdiği nesne. İlk örneği çalışan bir <xref:System.TimeZoneInfo> kullanarak kayıt defteri alarak nesne <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi. Saat dilimi oluşturulamaz, kodu katıştırılmış kaynak dosyasından alır.

Çünkü veri özel saat dilimi için (saat dilimlerini kullanarak örneği oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi) depolanmadığı kayıt defterinde, kod arama <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> saat dilimini Palmer, Antarktika örneklemek için. Bunun yerine, katıştırılmış kaynak dosyasına çağırmadan önce saat diliminin verileri içeren bir dizeyi almak için hemen görünür <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Projeye bir başvuru System.Windows.Forms.dll ve System.Core.dll eklenmesi gerektiğini.

* Şu ad alanlarından alınan olduğunu:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
- [Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)

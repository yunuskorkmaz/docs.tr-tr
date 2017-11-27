---
title: "Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db4f2ae40d25795b0e5f75ac3612f45834043dfa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme

Bu konuda, bir kaynak dosyasında kaydedilen saat dilimlerini geri yükleme açıklar. Bilgi ve saat dilimlerini kaydetme hakkında yönergeler için bkz: [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Katıştırılmış bir kaynaktan bir Timezoneınfo nesnesinin serisini kaldırmak için

1. Alınacak saat dilimi özel bir saat dilimi değilse, kullanarak örneği çalıştığınızda <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi.

2. Örneği bir <xref:System.Resources.ResourceManager> tam adını katıştırılmış kaynak dosyasını ve kaynak dosyası içeren bütünleştirilmiş kodun bir başvuru geçirerek nesnesi.

   Katıştırılmış kaynak dosyasının tam adı belirleyemiyorsa, kullanın [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derlemenin bildirimini incelemek için. Bir `.mresource` giriş kaynağı tanımlar. Örnekte, kaynağın tam adıdır `SerializeTimeZoneData.SerializedTimeZones`.

   Saat dilimi örneklemesi kodu içeren aynı bütünleştirilmiş kodda katıştırılmış kaynak dosyası varsa, çağırarak ona bir başvuru alabilirsiniz `static` (`Shared` Visual Basic'te) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi.

3. Varsa çağrısı <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi başarısız veya özel bir saat dilimi örneğinin oluşturulması için ise, çağırarak serileştirilmiş saat dilimi içeren bir dize almak <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> yöntemi.

4. Saat dilimi verileri seri durumdan çağırarak <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.

## <a name="example"></a>Örnek

Aşağıdaki örnek çıkarır bir <xref:System.TimeZoneInfo> katıştırılmış .NET XML kaynak dosyasında depolanan nesnesi.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Bu kod emin olmak için özel durum işleme gösterir bir <xref:System.TimeZoneInfo> uygulama tarafından gerekli nesne varsa. Örneği oluşturmak önce çalışır bir <xref:System.TimeZoneInfo> kayıt defteri kullanımından alma nesne <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi. Saat dilimi örneği varsa, kodu katıştırılmış kaynak dosyasından alır.

Çünkü özel saat dilimleri için verileri (saat dilimleri kullanarak örneği <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi) depolanmadığı kayıt defterinde, kod arama <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> Antarktika Palmer için saat dilimi örneği oluşturmak için. Bunun yerine, hemen çağırmadan önce saat diliminin veri içeren bir dize almak için katıştırılmış kaynak dosyası görünüyor. <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Windows.Forms.dll ve System.Core.dll projeye eklenmesini.

* Şu ad alanlarından alınan olduğunu:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)

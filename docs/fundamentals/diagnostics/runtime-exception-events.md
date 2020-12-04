---
title: Özel durum çalışma zamanı olayları
description: Özel durumlara ve özel durum işlemeye özgü tanılama bilgilerini toplayıp .NET çalışma zamanı olaylarına bakın.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96590033"
---
# <a name="net-runtime-exception-events"></a>.NET çalışma zamanı özel durum olayları

Bu çalışma zamanı olayları, oluşturulan özel durumlarla ilgili bilgileri yakalar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)

## <a name="exceptionthrown_v1-event"></a>ExceptionThrown_V1 olayı

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` 0x8000|Hata (1)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|80|Yönetilen bir özel durum oluşturulur.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|Özel durumun türü; Örneğin, `System.NullReferenceException` .|
|`ExceptionMessage`|`win:UnicodeString`|Gerçek özel durum iletisi.|
|`EIPCodeThrow`|`win:Pointer`|Özel durumun oluştuğu yönerge işaretçisi.|
|`ExceptionHR`|`win:UInt32`|Özel durum [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|
|`ExceptionFlags`|`win:UInt16`|`0x01`: HasInnerException.<br /><br /> `0x02`: IsNestedException.<br /><br /> `0x04`: IsRethrownException.<br /><br /> `0x08`: Ibozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> `0x10`: Isclscompliant (öğesinden türetilen özel durum <xref:System.Exception> CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="exceptioncatchstart-event"></a>Exceptioncatch başlangıç olayı

Bu olay, yönetilen bir özel durum catch işleyicisi başladığında yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` 0x8000|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|250|Yönetilen bir özel durum, çalışma zamanı tarafından işlenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Özel durumun oluştuğu yönerge işaretçisi.|
|`MethodID`|`win:Pointer`|Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.|
|`MethodName`|`win:UnicodeString`|Özel durumun oluştuğu yöntemin adı.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="exceptioncatchstop-event"></a>Exceptioncatch durdurma olayı

Bu olay, yönetilen bir özel durum catch işleyicisi sona erdiğinde yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` 0x8000|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|251|Yönetilen bir özel durum yakalama işleyicisi bitti.|

## <a name="exceptionfinallystart-event"></a>ExceptionFinallyStart olayı

Bu olay yönetilen bir özel durum finally işleyicisi başladığında yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` 0x8000|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|252|Yönetilen bir özel durum, çalışma zamanı tarafından işlenir.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Özel durumun oluştuğu yönerge işaretçisi.|
|`MethodID`|`win:Pointer`|Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.|
|`MethodName`|`win:UnicodeString`|Özel durumun oluştuğu yöntemin adı.|
|`ClrInstanceID`|`win:UInt16`|CLR veya CoreCLR örneği için benzersiz KIMLIK.|

## <a name="exceptionfinallystop-event"></a>ExceptionFinallyStop olayı

Bu olay, yönetilen bir özel durum catch işleyicisi sona erdiğinde yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` 0x8000|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|253|Yönetilen bir özel durum finally işleyicisi bitti.|

## <a name="exceptionfilterstart-event"></a>ExceptionFilterStart olayı

Bu olay, yönetilen bir özel durum filtrelemesi başladığında yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` 0x8000|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|254|Yönetilen özel durum filtrelemesi başlar.|

|Alan adı|Veri türü|Açıklama|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|Özel durumun oluştuğu yönerge işaretçisi.|
|`MethodID`|`win:Pointer`|Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.|
|`MethodName`|`win:UnicodeString`|Özel durumun oluştuğu yöntemin adı.|
|`ClrInstanceID`|`win:UInt16`|CoreCLR örneği için benzersiz KIMLIK.|

## <a name="exceptionfilterstop-event"></a>ExceptionFilterStop olayı

Yönetilen özel durum filtrelemesi sona erdiğinde bu olay yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` 0x8000|Bilgilendirici (4)|

 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|255|Yönetilen özel durum filtreleme sona erer.|

## <a name="exceptionthrownstop-event"></a>ExceptionThrownStop olayı

Bu olay, çalışma zamanı oluşturulan yönetilen bir özel durumu işlemeye çalışırken yayınlanır.

|Olayı yükseltmek için anahtar sözcük|Level|
|-----------------------------------|-----------|
|`ExceptionKeyword` 0x8000|Bilgilendirici (4)|
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.

|Olay|Olay Kimliği|Ne zaman oluşturulur|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|256|Yönetilen özel durum filtreleme sona erer.|

---
title: 'Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme'
description: COM metotlarından döndürülen HRESULT değerlerini .NET yöntemleri tarafından oluşturulan özel durumlara nasıl eşleneceğini inceleyin. Çalışma zamanı, COM ve .NET arasındaki geçişi işler.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
ms.openlocfilehash: 13798de1547428d54c10f83c41a5a402e2b3fb53
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872411"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme

COM yöntemleri, HRESULTs döndüren hataları raporlar; .NET yöntemleri özel durumlar oluşturarak bunları raporlar. Çalışma zamanı, iki arasındaki geçişi işler. .NET Framework her bir özel durum sınıfı bir HRESULT ile eşlenir.

 Kullanıcı tanımlı özel durum sınıfları, hangi HRESULT 'nin uygun olduğunu belirtebilir. Bu özel durum sınıfları özel durum nesnesi üzerindeki alanı ayarlanarak, özel durum oluşturulduğunda döndürülecek HRESULT öğesini dinamik olarak değiştirebilir `HResult` . Özel durum hakkında ek bilgi, `IErrorInfo` yönetilmeyen işlemdeki .net nesnesine uygulanan arabirimi aracılığıyla istemciye sağlanır.

 ' İ genişleten bir sınıf oluşturursanız `System.Exception` , oluşturma SıRASıNDA HRESULT alanını ayarlamanız gerekir. Aksi takdirde, temel sınıf HRESULT değerini atar. Yeni özel durum sınıflarını, özel durumun oluşturucusunda değeri sağlayarak mevcut bir HRESULT ile eşleyebilirsiniz.

 Çalışma zamanının bazen `HRESULT` iş parçacığında mevcut olduğu durumlarda zaman içindeki durumları yoksaydığına unutmayın `IErrorInfo` .  Bu davranış, `HRESULT` ve ' nin `IErrorInfo` aynı hatayı temsil etmediği durumlarda gerçekleşebilir.

### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Yeni bir özel durum sınıfı oluşturmak ve bunu bir HRESULT ile eşlemek için

1. Adlı yeni bir özel durum sınıfı oluşturmak ve bunu HRESULT ile eşlemek için aşağıdaki kodu kullanın `NoAccessException` `E_ACCESSDENIED` .

    ```cpp
    Class NoAccessException : public ApplicationException
    {
        NoAccessException () {
        HResult = E_ACCESSDENIED;
    }
    }
    CMyClass::MethodThatThrows
    {
    throw new NoAccessException();
    }
    ```

 Aynı anda hem yönetilen hem de yönetilmeyen kodu kullanan bir programla (herhangi bir programlama dilinde) karşılaşabilirsiniz. Örneğin, aşağıdaki kod örneğinde özel sıralayıcı, `Marshal.ThrowExceptionForHR(int HResult)` belirli BIR HRESULT değeri ile özel durum oluşturmak için yöntemini kullanır. Yöntemi HRESULT arar ve uygun özel durum türünü oluşturur. Örneğin, aşağıdaki kod parçasındaki HRESULT oluşturulur `ArgumentException` .

```cpp
CMyClass::MethodThatThrows
{
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);
}
```

 Aşağıdaki tabloda, HRESULT 'den, .NET 'teki karşılaştırılabilir özel durum sınıfına ortak eşlemeler sağlanmaktadır. Açık eşlemeler olmadan HRESULT değerleri ile eşleştirilir `COMException` . Tam güncel eşleme, [DotNet/Runtime deposunda](https://github.com/dotnet/runtime/blob/main/src/coreclr/vm/rexcep.h)bulunabilir.

|HRESULT|.NET özel durumu|
|-------------|--------------------|
|`COR_E_APPLICATION`|`ApplicationException`|
|`COR_E_ARGUMENT` veya `E_INVALIDARG`|`ArgumentException`|
|`COR_E_ARGUMENTOUTOFRANGE`|`ArgumentOutOfRangeException`|
|`COR_E_ARITHMETIC or ERROR_ARITHMETIC_OVERFLOW`|`ArithmeticException`|
|`COR_E_ARRAYTYPEMISMATCH`|`ArrayTypeMismatchException`|
|`COR_E_BADIMAGEFORMAT or ERROR_BAD_FORMAT`|`BadImageFormatException`|
|`COR_E_DIRECTORYNOTFOUND or ERROR_PATH_NOT_FOUND`|`DirectoryNotFoundException`|
|`COR_E_DIVIDEBYZERO`|`DivideByZeroException`|
|`COR_E_DUPLICATEWAITOBJECT`|`DuplicateWaitObjectException`|
|`COR_E_ENDOFSTREAM`|`EndOfStreamException`|
|`COR_E_ENTRYPOINTNOTFOUND`|`EntryPointNotFoundException`|
|`COR_E_EXCEPTION`|`Exception`|
|`COR_E_EXECUTIONENGINE`|`ExecutionEngineException`|
|`COR_E_FIELDACCESS`|`FieldAccessException`|
|`COR_E_FILENOTFOUND or ERROR_FILE_NOT_FOUND`|`FileNotFoundException`|
|`COR_E_FORMAT`|`FormatException`|
|`COR_E_INDEXOUTOFRANGE`|`IndexOutOfRangeException`|
|`COR_E_INVALIDCAST or E_NOINTERFACE`|`InvalidCastException`|
|`COR_E_INVALIDFILTERCRITERIA`|`InvalidFilterCriteriaException`|
|`COR_E_INVALIDOPERATION`|`InvalidOperationException`|
|`COR_E_IO`|`IOException`|
|`COR_E_MEMBERACCESS`|`AccessException`|
|`COR_E_METHODACCESS`|`MethodAccessException`|
|`COR_E_MISSINGFIELD`|`MissingFieldException`|
|`COR_E_MISSINGMANIFESTRESOURCE`|`MissingManifestResourceException`|
|`COR_E_MISSINGMEMBER`|`MissingMemberException`|
|`COR_E_MISSINGMETHOD`|`MissingMethodException`|
|`COR_E_NOTFINITENUMBER`|`NotFiniteNumberException`|
|`E_NOTIMPL`|`NotImplementedException`|
|`COR_E_NOTSUPPORTED`|`NotSupportedException`|
|`COR_E_NULLREFERENCE orE_POINTER`|`NullReferenceException`|
|`COR_E_OUTOFMEMORY or`<br /><br /> `E_OUTOFMEMORY`|`OutOfMemoryException`|
|`COR_E_OVERFLOW`|`OverflowException`|
|`COR_E_PATHTOOLONG or ERROR_FILENAME_EXCED_RANGE`|`PathTooLongException`|
|`COR_E_RANK`|`RankException`|
|`COR_E_REFLECTIONTYPELOAD`|`ReflectionTypeLoadException`|
|`COR_E_SECURITY`|`SecurityException`|
|`COR_E_SERIALIZATION`|`SerializationException`|
|`COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW`|`StackOverflowException`|
|`COR_E_SYNCHRONIZATIONLOCK`|`SynchronizationLockException`|
|`COR_E_SYSTEM`|`SystemException`|
|`COR_E_TARGET`|`TargetException`|
|`COR_E_TARGETINVOCATION`|`TargetInvocationException`|
|`COR_E_TARGETPARAMCOUNT`|`TargetParameterCountException`|
|`COR_E_THREADINTERRUPTED`|`ThreadInterruptedException`|
|`COR_E_THREADSTATE`|`ThreadStateException`|
|`COR_E_TYPELOAD`|`TypeLoadException`|
|`COR_E_TYPEINITIALIZATION`|`TypeInitializationException`|
|`COR_E_VERIFICATION`|`VerificationException`|

 Genişletilmiş hata bilgilerini almak için, yönetilen istemci, oluşturulan özel durum nesnesinin alanlarını incelemeli. Bir hata hakkında yararlı bilgiler sağlamak için özel durum nesnesi için, COM nesnesinin arabirimini uygulaması gerekir `IErrorInfo` . Çalışma zamanı, `IErrorInfo` özel durum nesnesini başlatmak için tarafından belirtilen bilgileri kullanır.

 COM nesnesi desteklemiyorsa `IErrorInfo` , çalışma zamanı varsayılan değerlerle bir özel durum nesnesi başlatır. Aşağıdaki tabloda bir özel durum nesnesiyle ilişkili her alan listelenmekte ve COM nesnesi desteklediğinde varsayılan bilgilerin kaynağı tanımlanmaktadır `IErrorInfo` .

 Çalışma zamanının bazen `HRESULT` iş parçacığında mevcut olduğu durumlarda zaman içindeki durumları yoksaydığına unutmayın `IErrorInfo` .  Bu davranış, `HRESULT` ve ' nin `IErrorInfo` aynı hatayı temsil etmediği durumlarda gerçekleşebilir.

|Özel durum alanı|COM 'tan bilgi kaynağı|
|---------------------|------------------------------------|
|`ErrorCode`|HRESULT çağrıdan döndürüldü.|
|`HelpLink`|`IErrorInfo->HelpContext`Sıfır değilse, dize birleştirerek `IErrorInfo->GetHelpFile` ve "#" ile oluşturulur `IErrorInfo->GetHelpContext` . Aksi takdirde dize öğesinden döndürülür `IErrorInfo->GetHelpFile` .|
|`InnerException`|Her zaman bir null başvurusu ( `Nothing` Visual Basic).|
|`Message`|Dize döndürüldü `IErrorInfo->GetDescription` .|
|`Source`|Dize döndürüldü `IErrorInfo->GetSource` .|
|`StackTrace`|Yığın izleme.|
|`TargetSite`|Hatalı HRESULT döndüren metodun adı.|

 , Ve gibi özel durum `Message` alanları `Source` `StackTrace` için kullanılamaz `StackOverflowException` .

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş COM birlikte çalışabilirlik](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Özel durumlar](../../standard/exceptions/index.md)

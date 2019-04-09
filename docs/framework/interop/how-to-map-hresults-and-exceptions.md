---
title: 'Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 609f7f6e5460bf315b87725405496e95abbfdd95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102771"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme
COM yöntemleri HRESULTs döndürerek hata raporu; .NET yöntemleri bunları özel durumları atma tarafından rapor. Çalışma zamanı, ikisi arasındaki geçişi işler. .NET Framework içindeki her bir özel durum sınıfı için HRESULT eşler.  
  
 Kullanıcı tanımlı özel durum sınıfları HRESULT uygun ne olursa olsun belirtebilirsiniz. Bu özel durum sınıfları dinamik olarak ayarlayarak özel durum oluşturulduğunda döndürülecek HRESULT değiştirebilirsiniz **HResult** alanına özel durum nesnesi. Özel durum hakkında ek bilgi istemcisi üzerinden sağlanan **IErrorInfo** yönetilmeyen işleminde .NET nesne üzerinde uygulanan arabirimi.  
  
 Genişleten bir sınıfı oluşturursanız **System.Exception**, yapım sırasında HRESULT alanını ayarlamanız gerekir. Aksi takdirde, temel sınıf HRESULT değerini atar. Özel durumun oluşturucusunu değeri sağlanarak yeni özel durum sınıfları için mevcut bir HRESULT eşleyebilirsiniz.  
  
 Çalışma zamanı bazen yoksayacak Not bir `HRESULT` durumda olduğu bir `IErrorInfo` iş parçacığı üzerinde mevcut.  Bu davranış durumlarda oluşabilir burada `HRESULT` ve `IErrorInfo` aynı hatayı temsil etmiyor.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Yeni bir özel durum sınıfı oluşturun ve bir HRESULT eşlemek için  
  
1.  Adlı yeni bir özel durum sınıfı oluşturmak için aşağıdaki kodu kullanın `NoAccessException` ve HRESULT harita `E_ACCESSDENIED`.  
  
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
  
 Aynı anda hem yönetilen hem de yönetilmeyen kodu kullanan bir programda (herhangi bir programlama dilini) hatalarla karşılaşabilirsiniz. Örneğin, aşağıdaki kod örneğinde özel sıralayıcı kullanır **Marshal.ThrowExceptionForHR (int HResult)** belirli bir HRESULT değerine sahip bir özel durum için yöntemi. Yöntem HRESULT arar ve uygun özel durum türü oluşturur. Örneğin, aşağıdaki kod parçası HRESULT oluşturur **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Aşağıdaki tablo, .NET Framework'teki karşılaştırılabilir özel durum sınıfına her HRESULT tam eşleme sağlar.  
  
|HRESULT|.NET özel durumu|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR_E_APPLICATION**|**ApplicationException**|  
|**COR_E_ARGUMENT veya E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**Üretiliyor**|  
|**COR_E_ARITHMETIC veya ERROR_ARITHMETIC_OVERFLOW**|**ArithmeticException**|  
|**COR_E_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT veya ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**CryptographicException**|  
|**COR_E_DIRECTORYNOTFOUND veya ERROR_PATH_NOT_FOUND**|**DirectoryNotFoundException**|  
|**COR_E_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR_E_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR_E_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR_E_EXCEPTION**|**Özel Durum**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND veya ERROR_FILE_NOT_FOUND**|**Derleme işlemi FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST veya e_noınterface**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**Ioexception**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**MissingFieldException**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR_E_MISSINGMEMBER**|**MissingMemberException**|  
|**COR_E_MISSINGMETHOD**|**MissingMethodException**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException**|  
|**COR_E_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E_NOTIMPL**|**NotImplementedException**|  
|**COR_E_NOTSUPPORTED**|**NotSupportedException**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY veya**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG veya ERROR_FILENAME_EXCED_RANGE**|**Pathtoolongexception'ı**|  
|**COR_E_RANK**|**RankException**|  
|**COR_E_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**RemotingException**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException**|  
|**COR_E_SECURITY**|**SecurityException**|  
|**COR_E_SERIALIZATION**|**SerializationException**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**StackOverflowException**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**SynchronizationLockException**|  
|**COR_E_SYSTEM**|**SystemException**|  
|**COR_E_TARGET**|**TargetException**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**TargetParameterCountException**|  
|**COR_E_THREADABORTED**|**ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**Threadınterruptedexception**|  
|**COR_E_THREADSTATE**|**ThreadStateException**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException**|  
|**COR_E_TYPEINITIALIZATION**|**Typeınitializationexception**|  
|**COR_E_VERIFICATION**|**VerificationException**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Diğer tüm HRESULTs**|**COMException**|  
  
 Genişletilmiş hata bilgilerini almak için yönetilen istemciyi oluşturulmasına neden olan özel durum nesnesi alanlarını incelemeniz gerekir. Özel durum nesnesi bir hata hakkında yararlı bilgiler sağlayan COM nesnesi uygulamalıdır **IErrorInfo** arabirimi. Çalışma zamanı tarafından sağlanan bilgileri kullanır **IErrorInfo** özel durum nesnesi başlatılamıyor.  
  
 COM nesnesi desteklemiyorsa **IErrorInfo**, çalışma zamanı bir özel durum nesnesi varsayılan değerlerle başlatır. Aşağıdaki tabloda, bir özel durum nesnesiyle ilişkilendirilen her bir alan listeler ve COM nesnesi desteklediğinde varsayılan bilgi kaynağını tanımlayan **IErrorInfo**.  
  
 Çalışma zamanı bazen yoksayacak Not bir `HRESULT` durumda olduğu bir `IErrorInfo` iş parçacığı üzerinde mevcut.  Bu davranış durumlarda oluşabilir burada `HRESULT` ve `IErrorInfo` aynı hatayı temsil etmiyor.  
  
|Özel alan|COM bilgisi kaynağı|  
|---------------------|------------------------------------|  
|**ErrorCode**|Çağrıdan HRESULT döndürdü.|  
|**HelpLink**|Varsa **IErrorInfo -> HelpContext** olan sıfır değilse, dize birleştirerek biçimlendirilmiş **IErrorInfo GetHelpFile ->** ve "#" ve **IErrorInfo -> GetHelpContext**. Aksi takdirde dize öğesinden döndürülen **IErrorInfo -> GetHelpFile**.|  
|**InnerException**|Her zaman null başvuru (**hiçbir şey** Visual Basic'te).|  
|**İleti**|Döndürülen dize **IErrorInfo -> GetDescription**.|  
|**Kaynak**|Döndürülen dize **IErrorInfo -> GetSource**.|  
|**Yığın izleme**|Yığın izleme.|  
|**TARGETSITE**|Başarısız olan döndürülen yöntemin adını HRESULT.|  
  
 Gibi özel alanları **ileti**, **kaynak**, ve **StackTrace** kullanılamaz **StackOverflowException**.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş COM Birlikte Çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Özel Durumlar](../../standard/exceptions/index.md)

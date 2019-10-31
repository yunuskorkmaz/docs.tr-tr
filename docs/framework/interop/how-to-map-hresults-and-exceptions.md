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
ms.openlocfilehash: 13dcca5f35750ad3e8bd6ea4f6dd443fe9a8ee94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123874"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme
COM yöntemleri, HRESULTs döndüren hataları raporlar; .NET yöntemleri özel durumlar oluşturarak bunları raporlar. Çalışma zamanı, iki arasındaki geçişi işler. .NET Framework her bir özel durum sınıfı bir HRESULT ile eşlenir.  
  
 Kullanıcı tanımlı özel durum sınıfları, hangi HRESULT 'nin uygun olduğunu belirtebilir. Bu özel durum sınıfları özel durum nesnesi üzerinde **HRESULT** alanı ayarlanarak, özel durum OLUŞTURULDUĞUNDA döndürülecek HRESULT öğesini dinamik olarak değiştirebilir. Özel durumla ilgili ek bilgiler, yönetilmeyen işlemdeki .NET nesnesine uygulanan **IErrorInfo** arabirimi aracılığıyla istemciye sağlanır.  
  
 **System. Exception**'ı genişleten bir sınıf oluşturursanız, oluşturma sırasında HRESULT alanını ayarlamanız gerekir. Aksi takdirde, temel sınıf HRESULT değerini atar. Yeni özel durum sınıflarını, özel durumun oluşturucusunda değeri sağlayarak mevcut bir HRESULT ile eşleyebilirsiniz.  
  
 Çalışma zamanının bazen iş parçacığında mevcut bir `IErrorInfo` olduğu durumlarda `HRESULT` yoksaydığına unutmayın.  Bu davranış, `HRESULT` ve `IErrorInfo` aynı hatayı temsil etmediği durumlarda meydana gelebilir.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Yeni bir özel durum sınıfı oluşturmak ve bunu bir HRESULT ile eşlemek için  
  
1. `NoAccessException` adlı yeni bir özel durum sınıfı oluşturmak ve bunu HRESULT `E_ACCESSDENIED`eşlemek için aşağıdaki kodu kullanın.  
  
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
  
 Aynı anda hem yönetilen hem de yönetilmeyen kodu kullanan bir programla (herhangi bir programlama dilinde) karşılaşabilirsiniz. Örneğin, aşağıdaki kod örneğinde özel sıralayıcı, belirli bir HRESULT değeri ile özel durum oluşturmak için **Marshal. ThrowExceptionForHR (INT HRESULT)** yöntemini kullanır. Yöntemi HRESULT arar ve uygun özel durum türünü oluşturur. Örneğin, aşağıdaki kod parçasındaki HRESULT **ArgumentException**üretir.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Aşağıdaki tabloda, her HRESULT 'den karşılaştırılabilen özel durum sınıfına .NET Framework tüm eşleme sağlanmıştır.  
  
|HRESULT|.NET özel durumu|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR_E_APPLICATION**|**ApplicationException**|  
|**COR_E_ARGUMENT veya E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
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
|**COR_E_EXCEPTION**|**Duruma**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND veya ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**Lıklarını**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST veya E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR_E_INVALIDOPERATION**|**Durumunu**|  
|**COR_E_IO**|**IOException**|  
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
|**COR_E_NULLREFERENCE orE_POINTER**|**Durumu**|  
|**COR_E_OUTOFMEMORY veya**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG veya ERROR_FILENAME_EXCED_RANGE**|**PathTooLongException**|  
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
|**COR_E_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR_E_THREADSTATE**|**ThreadStateException**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException**|  
|**COR_E_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR_E_VERIFICATION**|**VerificationException**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Diğer tüm HRESULTs 'lar**|**COMException**|  
  
 Genişletilmiş hata bilgilerini almak için, yönetilen istemci, oluşturulan özel durum nesnesinin alanlarını incelemeli. Bir hata hakkında yararlı bilgiler sağlamak için özel durum nesnesi için, COM nesnesi **IErrorInfo** arabirimini gerçekleştirmelidir. Çalışma zamanı, özel durum nesnesini başlatmak için **IErrorInfo** tarafından belirtilen bilgileri kullanır.  
  
 COM nesnesi **IErrorInfo**'yu desteklemiyorsa, çalışma zamanı varsayılan değerlerle bir özel durum nesnesi başlatır. Aşağıdaki tabloda bir özel durum nesnesiyle ilişkili her alan listelenmekte ve COM nesnesi **IErrorInfo 'yu**desteklediğinde varsayılan bilgilerin kaynağını tanımlıyor.  
  
 Çalışma zamanının bazen iş parçacığında mevcut bir `IErrorInfo` olduğu durumlarda `HRESULT` yoksaydığına unutmayın.  Bu davranış, `HRESULT` ve `IErrorInfo` aynı hatayı temsil etmediği durumlarda meydana gelebilir.  
  
|Özel durum alanı|COM 'tan bilgi kaynağı|  
|---------------------|------------------------------------|  
|**Raporladı**|HRESULT çağrıdan döndürüldü.|  
|**HelpLink**|**Ierrorinfo-> HelpContext** sıfır değilse, dize **ıerrorınfo-> GetHelpFile** ve "#" ve **IErrorInfo-> GetHelpContext**şeklinde birleştirerek oluşturulur. Aksi takdirde, dize **IErrorInfo-> GetHelpFile**öğesinden döndürülür.|  
|**Bakın**|Her zaman bir null başvurusu (Visual Basic**hiçbir şey** ).|  
|**İleti**|**IErrorInfo-> GetDescription**öğesinden döndürülen dize.|  
|**Kaynaktaki**|**IErrorInfo-> GetSource**öğesinden döndürülen dize.|  
|**StackTrace**|Yığın izleme.|  
|**TargetSite**|Hatalı HRESULT döndüren metodun adı.|  
  
 **İleti**, **kaynak**ve **StackTrace** gibi özel durum alanları **StackOverflowException**için kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş COM birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Özel Durumlar](../../standard/exceptions/index.md)

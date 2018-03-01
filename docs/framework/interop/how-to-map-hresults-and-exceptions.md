---
title: "Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 736e86e3013f34997be7ecf73ff4436675d4c05f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-map-hresults-and-exceptions"></a>Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme
COM yöntemleri HRESULTs döndürerek hata raporu; .NET yöntemleri bunları özel durumları atma tarafından rapor. Çalışma zamanı iki arasında geçiş işler. .NET Framework'teki her özel durum sınıfı bir HRESULT eşler.  
  
 Kullanıcı tanımlı özel durum sınıfları HRESULT uygun ne olursa olsun belirtebilirsiniz. Bu özel durum sınıfları dinamik olarak ayarlayarak özel durum oluşturulduğunda döndürülecek HRESULT değiştirebilirsiniz **HResult** özel durum nesnesi üzerinde alan. Özel durum hakkında ek bilgi istemcisi üzerinden sağlanan **IErrorInfo** yönetilmeyen işleminde .NET nesnesinde uygulanan arabirim.  
  
 Genişleten bir sınıfı oluşturursanız **System.Exception**, HRESULT alanını oluşturma sırasında ayarlamanız gerekir. Aksi takdirde, temel sınıf HRESULT değeri atar. Özel durumun Oluşturucusu değerinde sağlayarak mevcut HRESULT yeni özel durum sınıfları eşleyebilirsiniz.  
  
 Çalışma zamanı bazen yoksayacak Not bir `HRESULT` durumda olduğu bir `IErrorInfo` iş parçacığı mevcut.  Bu davranış durumlarda oluşabilir nerede `HRESULT` ve `IErrorInfo` aynı hatayı temsil etmiyor.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Yeni bir özel durum sınıfı oluşturmak ve bir HRESULT eşlemek için  
  
1.  Adlı yeni bir özel durum sınıfı oluşturmak için aşağıdaki kodu kullanın `NoAccessException` ve HRESULT eşleme `E_ACCESSDENIED`.  
  
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
  
 Aynı anda hem yönetilen hem de yönetilmeyen kodu kullanan bir programda (herhangi bir programlama dili) karşılaşabilirsiniz. Örneğin, aşağıdaki kod örneğinde özel sıralayıcı kullanır **Marshal.ThrowExceptionForHR (int HResult)** yöntemi belirli HRESULT değerine sahip bir özel durum. Yöntem HRESULT arar ve uygun özel durum türü oluşturur. Örneğin, aşağıdaki kod parçası olarak HRESULT oluşturur **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Aşağıdaki tabloda, tam eşleme karşılaştırılabilir özel durum sınıfındaki .NET Framework'teki her HRESULT sağlar.  
  
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
|**COR_E_EXCEPTION**|**Özel durumu**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND veya ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST veya E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
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
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
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
|**COR_E_TYPEINITIALIZATION**|**Typeınitializationexception**|  
|**COR_E_VERIFICATION**|**VerificationException**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Diğer tüm HRESULTs**|**COMException**|  
  
 Genişletilmiş hata bilgileri almak için yönetilen istemci oluşturulan özel durum nesnesi alanları incelemeniz gerekir. Özel durum nesnesi bir hata hakkında yararlı bilgiler sağlayan COM nesnesi uygulamalıdır **IErrorInfo** arabirimi. Çalışma zamanı tarafından sağlanan bilgileri kullanır **IErrorInfo** özel durum nesnesi başlatılamadı.  
  
 COM nesnesi desteklemediği varsa **IErrorInfo**, çalışma zamanı bir özel durum nesnesi varsayılan değerlerle başlatır. Aşağıdaki tabloda, bir özel durum nesnesi ile ilişkili her alanı listeler ve COM nesnesi desteklediğinde varsayılan bilgileri kaynağını tanımlayan **IErrorInfo**.  
  
 Çalışma zamanı bazen yoksayacak Not bir `HRESULT` durumda olduğu bir `IErrorInfo` iş parçacığı mevcut.  Bu davranış durumlarda oluşabilir nerede `HRESULT` ve `IErrorInfo` aynı hatayı temsil etmiyor.  
  
|Özel alan|COM bilgilerinden kaynağı|  
|---------------------|------------------------------------|  
|**Hata kodu**|HRESULT çağrısından döndürüldü.|  
|**HelpLink**|Varsa **IErrorInfo HelpContext ->** olan sıfır olmayan, dize birleştirerek biçimlendirildiğinden **IErrorInfo -> GetHelpFile** ve "#" ve **IErrorInfo -> GetHelpContext**. Aksi takdirde gelen dize döndürülür **IErrorInfo -> GetHelpFile**.|  
|**InnerException**|Her zaman bir null başvuru (**hiçbir şey** Visual Basic'te).|  
|**İleti**|Döndürülen dize **IErrorInfo -> GetDescription**.|  
|**Kaynak**|Döndürülen dize **IErrorInfo -> GetSource**.|  
|**StackTrace**|Yığın izleme.|  
|**TargetSite**|Başarısız olan döndürülen yöntemin adını HRESULT.|  
  
 Özel alanlar, gibi **ileti**, **kaynak**, ve **StackTrace** kullanılamaz **StackOverflowException**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş COM birlikte çalışabilirliği](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Özel Durumlar](../../../docs/standard/exceptions/index.md)

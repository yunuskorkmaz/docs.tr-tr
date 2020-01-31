---
title: ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: 99e473268fd0d5bb8ce120b97576277949b86508
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869003"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi

Belirtilen Microsoft ara dili (MSIL) eşleme girdilerini kullanarak belirtilen işlev için bir kod Haritası ayarlar.

> [!NOTE]
> .NET Framework sürüm 2,0 ' de, belirli bir uygulama etki alanında genel bir işlevi temsil eden bir `FunctionID` `SetILInstrumentedCodeMap` çağırmak, uygulama etki alanındaki bu işlevin tüm örneklerini etkiler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>Parametreler

`functionId`\
'ndaki Kod eşlemesi ayarlanacak işlevin KIMLIĞI.

`fStartJit`\
'ndaki `SetILInstrumentedCodeMap` yöntemine yapılan çağrının, belirli bir `FunctionID`için ilk olup olmadığını belirten bir Boolean değer. Belirli bir `FunctionID`için `SetILInstrumentedCodeMap` ilk çağrıda `true` ve bundan sonra `false` için `fStartJit` ayarlayın.

`cILMapEntries`\
'ndaki `cILMapEntries` dizisindeki öğelerin sayısı.

`rgILMapEntries`\
'ndaki Her biri bir MSIL sapmasını belirten COR_IL_MAP yapıları dizisi.

## <a name="remarks"></a>Açıklamalar

Profil Oluşturucu genellikle bu yöntemi işaretlemek için (örneğin, belirli bir kaynak satırına ulaşıldığında bildirmek üzere) bir yöntemin kaynak koduna deyimler ekler. `SetILInstrumentedCodeMap`, profil oluşturucunun özgün MSIL talimatlarını yeni konumlarına eşlemesine olanak sağlar. Bir profil oluşturucu, belirli bir yerel kenar için özgün MSIL sapmasını almak üzere [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) metodunu kullanabilir.

Hata ayıklayıcı, her bir eski kaydırın orijinal, değiştirilmemiş MSIL kodu içindeki bir MSIL denkleşeceğini ve her yeni kaydırın yeni, belgelenmiş koddaki MSIL denkleşeceğini varsayacaktır. Haritanın artan sırada sıralanması gerekir. Adımlamayı düzgün şekilde çalışmak için aşağıdaki yönergeleri izleyin:

- Belgelenmiş MSIL kodunu yeniden düzenleme.

- Özgün MSIL kodunu kaldırmayın.

- Haritadaki program veritabanı (PDB) dosyasındaki tüm sıra noktalarına ait girişleri dahil edin. Eşleme, eksik girişleri enterpolamıyor. Bu nedenle, aşağıdaki haritada verilmiştir:

  (0 eski, 0 yeni)

  (5 eski, 10 yeni)

  (9 eski, 20 yeni)

  - 0, 1, 2, 3 veya 4 ' ün eski bir kayması, 0 ' dan yeni bir uzaklığa eşlenecek.

  - 5, 6, 7 veya 8 ' in eski bir kayması, yeni %10 ' a eşlenir.

  - Daha eski bir 9 veya üzeri fark, 20. yeni uzaklığa eşlenir.

  - 0, 1, 2, 3, 4, 5, 6, 7, 8 ya da 9 ' un yeni bir kayması, 0 ' dan eski uzaklığa eşlenir.

  - 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 ' un yeni bir kayması, 5 eski uzaklığa eşlenir.

  - 20 veya üzeri yeni bir konum, eski konum 9 ' A eşlenir.

.NET Framework 3,5 ve önceki sürümlerde [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) yöntemini çağırarak `rgILMapEntries` dizisini ayırırsınız. Çalışma zamanı bu belleğin sahipliğini aldığı için profil oluşturucu onu serbest bırakmayı denememelidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)

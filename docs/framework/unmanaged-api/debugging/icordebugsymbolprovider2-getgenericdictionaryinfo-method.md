---
title: 'ICorDebugSymbolProvider2:: Getgenericdictionaryınfo yöntemi'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: a6c32b72c5924399aeb13d56ddf9242fe7990f35
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379316"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2:: Getgenericdictionaryınfo yöntemi

Genel sözlük eşlemesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a>Parametreler

`ppMemoryBuffer`\
dışı Genel sözlük eşlemesini içeren bir [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) nesnesinin adresine yönelik bir işaretçi. Daha fazla bilgi için Açıklamalar bölümüne bakın.

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.

Eşleme iki üst düzey bölümden oluşur:

- Bu haritaya dahil olan tüm sözlüklerin göreli sanal adreslerini (RVA) içeren bir [Dizin](#Directory) .

- Nesne örneği oluşturma bilgilerini içeren bayt hizalanmış [yığın](#Heap) . Son dizin girdisinden hemen sonra başlar.

<a name="Directory"></a>

## <a name="the-directory"></a>Dizin

Dizindeki her giriş, yığın içindeki bir uzaklığa başvurur; diğer bir deyişle, yığının başlangıcına göre bir uzaklıkdır. Tek tek girişlerin değeri benzersiz değildir; birden çok dizin girişinin yığında aynı sapmayı göstermesi mümkündür.

Genel sözlük eşlemesinin dizin bölümü aşağıdaki yapıya sahiptir:

- İlk 4 bayt sözlük girişi sayısını (yani, Sözlükteki göreli sanal adreslerin sayısını) içerir. Bu değere *N*olarak başvuracağız. Yüksek bit ayarlandıysa, girişler göreli sanal adrese göre artan sırada sıralanır.

- *N* Dizin girdileri izler. Her giriş, iki 4 baytlık kesimde 8 bayttan oluşur:

  - Bayt 0-3: RVA; sözlüğün göreli sanal adresi.

  - Bayt 4-7: konum; yığının başlangıcına göre bir göreli konum.

<a name="Heap"></a>

## <a name="the-heap"></a>Yığın

Yığın boyutu + 4 dizin boyutundan akışın uzunluğu çıkartılacak şekilde bir akış okuyucusu tarafından hesaplanabilir. Diğer bir deyişle:

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

Dizin boyutunun nerede olduğu `N * 8` .

Yığındaki her bir örnek oluşturma bilgi öğesinin biçimi:

- Bu örnek oluşturma bilgi öğesinin sıkıştırılmış ECMA meta veri biçimindeki bayt cinsinden uzunluğu. Değer bu uzunluk bilgilerini dışlar.

- Sıkıştırılmış ECMA meta veri biçimindeki genel örnek oluşturma türlerinin veya *T*'nin sayısı.

- *T* türleri, her biri ECMA tür imza biçiminde gösterilir.

Her yığın öğesinin uzunluğunun dahil edilmesi, yığın etkilenmeden dizin bölümünün basit sıralanmasını mümkün.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorDebug. IDL, CorDebug. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugSymbolProvider2 Arabirimi](icordebugsymbolprovider2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

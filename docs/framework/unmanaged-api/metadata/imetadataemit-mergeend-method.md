---
title: IMetaDataEmit::MergeEnd Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: 34ecfc2f01f22971e135358806adeea632e02f8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448032"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd Yöntemi

[Imetadatayayma:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)için bir veya daha fazla önceki çağrı tarafından belirtilen tüm meta veri kapsamlarını geçerli kapsama birleştirir.

## <a name="syntax"></a>Sözdizimi

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>Parametreler

Bu yöntem hiçbir parametre alır.

## <a name="remarks"></a>Açıklamalar

Bu yordam, önceki `IMetaDataEmit::Merge`çağrıları tarafından belirtilen tüm içeri aktarma kapsamlarından geçerli çıkış kapsamına gerçek meta verilerin birleştirilmesini tetikler.

Aşağıdaki özel koşullar birleştirme için geçerlidir:

- İçeri aktarma kapsamındaki meta veriler için benzersiz olduğundan, bir modül sürümü tanımlayıcısı (MVıD) hiçbir şekilde içeri aktarılmaz.

- Modül genelinde mevcut özelliklerin üzerine yazılmaz.

  Geçerli kapsam için modül özellikleri zaten ayarlandıysa, hiçbir modül özelliği içeri aktarılmaz. Ancak, geçerli kapsamda modül özellikleri ayarlanmamışsa, ilk kez karşılaşıldığında yalnızca bir kez içeri aktarılır. Bu modül özelliklerine yeniden karşılaşılırsa, bunlar yinelemelerdir. Tüm modül özelliklerinin (MVıD hariç) değerleri karşılaştırılaysa ve yinelenen öğeler bulunmazsa bir hata oluşur.

- Tür tanımları (`TypeDef`) için, geçerli kapsamda birleştirilmemiş bir yineleme yok. `TypeDef` nesneler, *guıd* + *sürüm numarasına* + *tam nitelikli nesne adı* için yinelemeler için denetlenir. Ad veya GUID üzerinde bir eşleşme varsa ve diğer iki öğe farklıysa, bir hata oluşur. Aksi takdirde, üç öğe de eşleşiyorsa, girişlerin gerçekten yinelenen olduğundan emin olmak için `MergeEnd` bir Amna hatlarıyla denetimi yapar; Aksi takdirde bir hata oluşur. Bu Amna hatlarıyla denetimi şuna bakar:

  - Aynı sırada oluşan aynı üye bildirimleri. `mdPrivateScope` olarak işaretlenen Üyeler ( [Cormethodadttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) sabit listesine bakın) bu denetimi içermez; Bunlar özellikle birleştirilir.

  - Aynı sınıf düzeni.

  Bu, bir `TypeDef` nesnesinin bildirildiği her meta veri kapsamındaki her zaman tam ve tutarlı olarak tanımlanması gereken anlamına gelir; üye uygulamaları (bir sınıf için) birden çok derleme birimine yayıldığında, tam tanımın her kapsamda var olduğu varsayılır ve her bir kapsamda artımlı değildir. Örneğin, parametre adları sözleşmeyle ilgiliyse, her kapsama aynı şekilde yayılmaları gerekir; Bunlar ilgili değilse meta verilere yayılmamalıdır.

  Özel durum, bir `TypeDef` nesnesi, `mdPrivateScope`olarak işaretlenmiş artımlı üyelere sahip olabilir. Bunlarla karşılaşmadan `MergeEnd` yinelenenleri artırarak geçerli kapsama ekler. Derleyici özel kapsamı anladığından, derleyicinin kuralları zorlarken sorumlu olması gerekir.

- Göreli sanal adresler (RVA) içeri aktarılmaz veya birleştirilmez; Derleyicinin bu bilgileri yeniden yayma beklenmektedir.

- Özel öznitelikler yalnızca, eklendiği öğe birleştirildiğinde birleştirilir. Örneğin, bir sınıfla ilişkili özel öznitelikler, sınıf ilk kez karşılaşıldığında birleştirilir. Özel öznitelikler, derleme birimine özgü bir `TypeDef` veya `MemberDef` ilişkili ise (bir üye derlenmesi zaman damgası gibi), bunlar birleştirilmez ve söz konusu meta verileri kaldırmak veya güncelleştirmek için derleyiciye kadar olur.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** Cor. h

**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır

**.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

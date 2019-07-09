---
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo yöntemi
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65407fca73971546725d9457d25bf1270d2001e2
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662541"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="bb3fc-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb3fc-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="bb3fc-103">Genel bir sözlük harita alır.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb3fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb3fc-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="bb3fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb3fc-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="bb3fc-106">[out] Adresine bir işaretçi bir [Icordebugmemorybuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) genel bir sözlük harita içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="bb3fc-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb3fc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb3fc-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="bb3fc-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="bb3fc-110">Eşleme, üst düzey iki bölümden oluşur:</span><span class="sxs-lookup"><span data-stu-id="bb3fc-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="bb3fc-111">A [dizin](#Directory) bu dahil tüm sözlüklerin göreli sanal adreslerine (RVA) içeren.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="bb3fc-112">Bayt hizalı [yığın](#Heap) nesne oluşturmada bilgileri içeren.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="bb3fc-113">Son directory girişinin hemen sonra başlar.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="bb3fc-114">Dizin</span><span class="sxs-lookup"><span data-stu-id="bb3fc-114">The Directory</span></span>

<span data-ttu-id="bb3fc-115">Her giriş dizininde yığın içinde bir uzaklık başvuruyor; yani yığın başlangıç göre bir uzaklık değildir.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="bb3fc-116">Girişler değerini mutlaka benzersiz değil; birden çok dizin girdisi yığınındaki aynı uzaklık işaret edecek şekilde mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="bb3fc-117">Genel bir sözlük harita öğesinin dizin bölümü aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bb3fc-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="bb3fc-118">İlk 4 baytı dictionary girişlerinin (diğer bir deyişle, sözlükteki göreli sanal adreslerine sayısı) sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="bb3fc-119">Bu değer anılacaktır *N*. Yüksek bit ayarlanmışsa girişleri artan düzende göreli sanal adres göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="bb3fc-120">*N* dizin girdisi izleyin.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-120">The *N* directory entries follow.</span></span> <span data-ttu-id="bb3fc-121">Her girişin iki 4 baytlık Segment 8 baytlık oluşur:</span><span class="sxs-lookup"><span data-stu-id="bb3fc-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="bb3fc-122">Bayt 0-3: RVA; sözlüğün göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="bb3fc-123">4-7 baytlar: Uzaklık; yığın başlangıcını göre bir uzaklık.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="bb3fc-124">Yığın</span><span class="sxs-lookup"><span data-stu-id="bb3fc-124">The Heap</span></span>

<span data-ttu-id="bb3fc-125">Dizin boyutu + 4 akıştan uzunluğunu çıkararak göre bir akış okuyucusunu yığının boyutu hesaplanabilir.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="bb3fc-126">Diğer bir deyişle:</span><span class="sxs-lookup"><span data-stu-id="bb3fc-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="bb3fc-127">dizin boyutu olduğu `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="bb3fc-128">Yığındaki her örneklemesi bilgi öğesi için biçimi şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="bb3fc-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="bb3fc-129">Bu örnek oluşturma bilgi öğesi sıkıştırılmış ECMA meta veri biçimi bayt uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="bb3fc-130">Değeri, bu uzunluğu bilgileri içermez.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-130">The value excludes this length information.</span></span>

- <span data-ttu-id="bb3fc-131">Genel örnek oluşturma türleri sayısı veya *T*, sıkıştırılmış ECMA meta veri biçiminde.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="bb3fc-132">*T* türlerini, her temsil ECMA türü imza biçiminde.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="bb3fc-133">Her yığın öğe uzunluğu dahilini Basit Dizin bölümü yığın etkilemeden sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb3fc-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb3fc-134">Requirements</span></span>

<span data-ttu-id="bb3fc-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb3fc-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="bb3fc-136">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb3fc-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="bb3fc-137">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb3fc-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="bb3fc-138">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3fc-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bb3fc-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-139">See also</span></span>

- [<span data-ttu-id="bb3fc-140">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb3fc-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="bb3fc-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bb3fc-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

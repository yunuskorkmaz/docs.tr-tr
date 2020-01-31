---
title: 'ICorDebugSymbolProvider2:: Getgenericdictionaryınfo yöntemi'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: 02ecaf56e845680472f42c04f3978e54e7a69272
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791501"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="5b44a-102">ICorDebugSymbolProvider2:: Getgenericdictionaryınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b44a-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="5b44a-103">Genel sözlük eşlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="5b44a-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b44a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b44a-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="5b44a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b44a-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="5b44a-106">dışı Genel sözlük eşlemesini içeren bir [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b44a-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="5b44a-107">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5b44a-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b44a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b44a-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="5b44a-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b44a-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="5b44a-110">Eşleme iki üst düzey bölümden oluşur:</span><span class="sxs-lookup"><span data-stu-id="5b44a-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="5b44a-111">Bu haritaya dahil olan tüm sözlüklerin göreli sanal adreslerini (RVA) içeren bir [Dizin](#Directory) .</span><span class="sxs-lookup"><span data-stu-id="5b44a-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="5b44a-112">Nesne örneği oluşturma bilgilerini içeren bayt hizalanmış [yığın](#Heap) .</span><span class="sxs-lookup"><span data-stu-id="5b44a-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="5b44a-113">Son dizin girdisinden hemen sonra başlar.</span><span class="sxs-lookup"><span data-stu-id="5b44a-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="5b44a-114">Dizin</span><span class="sxs-lookup"><span data-stu-id="5b44a-114">The Directory</span></span>

<span data-ttu-id="5b44a-115">Dizindeki her giriş, yığın içindeki bir uzaklığa başvurur; diğer bir deyişle, yığının başlangıcına göre bir uzaklıkdır.</span><span class="sxs-lookup"><span data-stu-id="5b44a-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="5b44a-116">Tek tek girişlerin değeri benzersiz değildir; birden çok dizin girişinin yığında aynı sapmayı göstermesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5b44a-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="5b44a-117">Genel sözlük eşlemesinin dizin bölümü aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5b44a-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="5b44a-118">İlk 4 bayt sözlük girişi sayısını (yani, Sözlükteki göreli sanal adreslerin sayısını) içerir.</span><span class="sxs-lookup"><span data-stu-id="5b44a-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="5b44a-119">Bu değere *N*olarak başvuracağız. Yüksek bit ayarlandıysa, girişler göreli sanal adrese göre artan sırada sıralanır.</span><span class="sxs-lookup"><span data-stu-id="5b44a-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="5b44a-120">*N* Dizin girdileri izler.</span><span class="sxs-lookup"><span data-stu-id="5b44a-120">The *N* directory entries follow.</span></span> <span data-ttu-id="5b44a-121">Her giriş, iki 4 baytlık kesimde 8 bayttan oluşur:</span><span class="sxs-lookup"><span data-stu-id="5b44a-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="5b44a-122">Bayt 0-3: RVA; sözlüğün göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="5b44a-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="5b44a-123">Bayt 4-7: konum; yığının başlangıcına göre bir göreli konum.</span><span class="sxs-lookup"><span data-stu-id="5b44a-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="5b44a-124">Yığın</span><span class="sxs-lookup"><span data-stu-id="5b44a-124">The Heap</span></span>

<span data-ttu-id="5b44a-125">Yığın boyutu + 4 dizin boyutundan akışın uzunluğu çıkartılacak şekilde bir akış okuyucusu tarafından hesaplanabilir.</span><span class="sxs-lookup"><span data-stu-id="5b44a-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="5b44a-126">Diğer bir deyişle:</span><span class="sxs-lookup"><span data-stu-id="5b44a-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="5b44a-127">Dizin boyutunun `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="5b44a-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="5b44a-128">Yığındaki her bir örnek oluşturma bilgi öğesinin biçimi:</span><span class="sxs-lookup"><span data-stu-id="5b44a-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="5b44a-129">Bu örnek oluşturma bilgi öğesinin sıkıştırılmış ECMA meta veri biçimindeki bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="5b44a-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="5b44a-130">Değer bu uzunluk bilgilerini dışlar.</span><span class="sxs-lookup"><span data-stu-id="5b44a-130">The value excludes this length information.</span></span>

- <span data-ttu-id="5b44a-131">Sıkıştırılmış ECMA meta veri biçimindeki genel örnek oluşturma türlerinin veya *T*'nin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5b44a-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="5b44a-132">*T* türleri, her biri ECMA tür imza biçiminde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5b44a-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="5b44a-133">Her yığın öğesinin uzunluğunun dahil edilmesi, yığın etkilenmeden dizin bölümünün basit sıralanmasını mümkün.</span><span class="sxs-lookup"><span data-stu-id="5b44a-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="5b44a-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b44a-134">Requirements</span></span>

<span data-ttu-id="5b44a-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b44a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5b44a-136">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5b44a-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5b44a-137">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5b44a-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5b44a-138">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b44a-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5b44a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b44a-139">See also</span></span>

- [<span data-ttu-id="5b44a-140">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b44a-140">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="5b44a-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5b44a-141">Debugging Interfaces</span></span>](debugging-interfaces.md)

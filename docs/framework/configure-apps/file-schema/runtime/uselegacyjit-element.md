---
description: 'Daha fazla bilgi edinin: <useLegacyJit> öğesi'
title: <useLegacyJit> Öğesi
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a1449cbc69f0aa1b91cc427fbfc5b984bf605169
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640010"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="07092-103">\<useLegacyJit> Öğesi</span><span class="sxs-lookup"><span data-stu-id="07092-103">\<useLegacyJit> Element</span></span>

<span data-ttu-id="07092-104">Ortak dil çalışma zamanının, Just-In-Time derlemesi için eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="07092-104">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a><span data-ttu-id="07092-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="07092-105">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="07092-106">Öğe adı `useLegacyJit` büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="07092-106">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07092-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="07092-107">Attributes and elements</span></span>

<span data-ttu-id="07092-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07092-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07092-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07092-109">Attributes</span></span>  
  
| <span data-ttu-id="07092-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07092-110">Attribute</span></span> | <span data-ttu-id="07092-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07092-111">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="07092-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07092-112">Required attribute.</span></span><br><br><span data-ttu-id="07092-113">Çalışma zamanının eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="07092-113">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="07092-114">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="07092-114">enabled attribute</span></span>  
  
| <span data-ttu-id="07092-115">Değer</span><span class="sxs-lookup"><span data-stu-id="07092-115">Value</span></span> | <span data-ttu-id="07092-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07092-116">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="07092-117">0</span><span class="sxs-lookup"><span data-stu-id="07092-117">0</span></span>     | <span data-ttu-id="07092-118">Ortak dil çalışma zamanı, .NET Framework 4,6 ve sonraki sürümlerde bulunan yeni 64-bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="07092-118">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="07092-119">1</span><span class="sxs-lookup"><span data-stu-id="07092-119">1</span></span>     | <span data-ttu-id="07092-120">Ortak dil çalışma zamanı, eski 64 bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="07092-120">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="07092-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="07092-121">Child elements</span></span>

<span data-ttu-id="07092-122">Yok</span><span class="sxs-lookup"><span data-stu-id="07092-122">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="07092-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="07092-123">Parent elements</span></span>  
  
| <span data-ttu-id="07092-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="07092-124">Element</span></span>         | <span data-ttu-id="07092-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07092-125">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="07092-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="07092-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="07092-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="07092-127">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="07092-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07092-128">Remarks</span></span>  

<span data-ttu-id="07092-129">.NET Framework 4,6 ' den başlayarak, ortak dil çalışma zamanı, varsayılan olarak tam zamanında (JıT) derleme için yeni bir 64 bit derleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="07092-129">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="07092-130">Bazı durumlarda bu durum, 64 bit JıT derleyicisi 'nin önceki sürümü tarafından derlenen uygulama kodundan kaynaklanan bir farklılık oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="07092-130">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="07092-131">`enabled` `<useLegacyJit>` Öğesinin özniteliğini olarak ayarlayarak `1` , yeni 64-bit JIT derleyicisini devre dışı bırakabilir ve bunun yerine eskı 64 bit JIT derleyicisini kullanarak uygulamanızı derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07092-131">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07092-132">`<useLegacyJit>`Öğesi yalnızca 64 BITLIK JIT derlemesini etkiler.</span><span class="sxs-lookup"><span data-stu-id="07092-132">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="07092-133">32 bit JıT derleyicisi ile derleme etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="07092-133">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="07092-134">Yapılandırma dosyası ayarı kullanmak yerine, eski 64 bit JıT derleyicisini iki farklı şekilde etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="07092-134">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="07092-135">Ortam değişkenini ayarlama</span><span class="sxs-lookup"><span data-stu-id="07092-135">Setting an environment variable</span></span>

  <span data-ttu-id="07092-136">`COMPLUS_useLegacyJit`Ortam değişkenini ya `0` (yeni 64-bit JIT derleyicisini kullanın) veya `1` (eskı 64 bit JIT derleyicisini kullanın) olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="07092-136">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="07092-137">Ortam değişkeni *genel kapsama* sahiptir, yani makinede çalıştırılan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="07092-137">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="07092-138">Ayarlanırsa, uygulama yapılandırma dosyası ayarı tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="07092-138">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="07092-139">Ortam değişkeni adı büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="07092-139">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="07092-140">Kayıt defteri anahtarı ekleme</span><span class="sxs-lookup"><span data-stu-id="07092-140">Adding a registry key</span></span>

  <span data-ttu-id="07092-141">`REG_DWORD` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` Kayıt defterindeki veya anahtarına bir değer ekleyerek eski 64 bit JIT derleyicisini etkinleştirebilirsiniz `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` .</span><span class="sxs-lookup"><span data-stu-id="07092-141">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="07092-142">Değer olarak adlandırılır `useLegacyJit` .</span><span class="sxs-lookup"><span data-stu-id="07092-142">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="07092-143">Değer 0 ise, yeni derleyici kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07092-143">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="07092-144">Değer 1 ise, eski 64 bit JıT derleyicisi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07092-144">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="07092-145">Kayıt defteri değer adı büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="07092-145">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="07092-146">Değeri `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtara eklemek, makinede çalışan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="07092-146">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="07092-147">Değeri `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtara eklemek, geçerli kullanıcı tarafından çalıştırılan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="07092-147">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="07092-148">Bir makine birden çok kullanıcı hesabıyla yapılandırıldıysa, değer diğer kullanıcılar için de kayıt defteri anahtarlarına eklenmediği sürece yalnızca geçerli kullanıcı tarafından çalıştırılan uygulamalar etkilenir.</span><span class="sxs-lookup"><span data-stu-id="07092-148">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="07092-149">`<useLegacyJit>`Öğesini bir yapılandırma dosyasına eklemek, varsa kayıt defteri ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="07092-149">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07092-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="07092-150">Example</span></span>  

<span data-ttu-id="07092-151">Aşağıdaki yapılandırma dosyası, derlemeyi yeni 64-bit JıT derleyicisi ile devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="07092-151">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07092-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07092-152">See also</span></span>

- [<span data-ttu-id="07092-153">\<runtime> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="07092-153">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="07092-154">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="07092-154">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="07092-155">Risk azaltma: yeni 64-bit JıT derleyicisi</span><span class="sxs-lookup"><span data-stu-id="07092-155">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)

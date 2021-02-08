---
description: "Şu konuda daha fazla bilgi edinin: BC40029: ' ', <classname> <interfacename> uyguladığı ' ' arabirimi CLS uyumlu olmadığından CLS uyumlu değil"
title: Uyguladığı '<classname>' arabirimi CLS uyumlu olmadığından, '<interfacename>' CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 28264dd602bd20a6b33bebd965982ca12d402d01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796787"
---
# <a name="bc40029-classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a><span data-ttu-id="08b05-103">BC40029: ' ' \<classname> , \<interfacename> uyguladığı ' ' arabirimi CLS uyumlu olmadığından CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="08b05-103">BC40029: '\<classname>' is not CLS-compliant because the interface '\<interfacename>' it implements is not CLS-compliant</span></span>

<span data-ttu-id="08b05-104">Bir sınıf veya arabirim, `<CLSCompliant(True)>` veya olarak işaretlenen veya işaretlenmemiş bir türden türetildiklerinde olarak işaretlenir `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="08b05-104">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>

 <span data-ttu-id="08b05-105">Bir sınıf veya arabirimin, [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, tüm devralma hiyerarşisinin uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08b05-105">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="08b05-106">Bu, devralınan her türün doğrudan veya dolaylı olarak uyumlu olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="08b05-106">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="08b05-107">Benzer şekilde, bir sınıf bir veya daha fazla arabirim uygularsa bunların tümünün devralma hiyerarşileri boyunca uyumlu olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="08b05-107">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>

 <span data-ttu-id="08b05-108"><xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="08b05-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="08b05-109">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="08b05-109">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="08b05-110"><xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="08b05-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="08b05-111">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="08b05-111">By default, this message is a warning.</span></span> <span data-ttu-id="08b05-112">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="08b05-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="08b05-113">**Hata kimliği:** BC40029</span><span class="sxs-lookup"><span data-stu-id="08b05-113">**Error ID:** BC40029</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="08b05-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="08b05-114">To correct this error</span></span>

- <span data-ttu-id="08b05-115">CLS uyumluluğu gerekiyorsa, bu türü farklı bir devralma hiyerarşisi veya uygulama şeması içinde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="08b05-115">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>

- <span data-ttu-id="08b05-116">Bu türün geçerli devralma hiyerarşisinde veya uygulama düzeninde kalmasını istiyorsanız, ' ın <xref:System.CLSCompliantAttribute> tanımını kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="08b05-116">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>

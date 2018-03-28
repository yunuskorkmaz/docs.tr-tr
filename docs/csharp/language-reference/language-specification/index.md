---
title: C# 6.0 taslak dil belirtimi
ms.date: 07/01/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: reference
helpviewer_keywords:
- C# language, specification
- what's new [C#], language specification
- Visual C#, C# language specification
- language specification [C#]
ms.assetid: e5d5a5cc-636b-4bff-b9c8-a8edc6207c22
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 98c0ae41d9c29238f364d3bfcecc193c6a391149
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="c-60-draft-language-specification"></a><span data-ttu-id="5c45b-102">C# 6.0 taslak dil belirtimi</span><span class="sxs-lookup"><span data-stu-id="5c45b-102">C# 6.0 draft Language Specification</span></span>
<span data-ttu-id="5c45b-103">C# dil belirtimi C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="5c45b-103">The C# Language Specification is the definitive source for C# syntax and usage.</span></span> <span data-ttu-id="5c45b-104">Bu belirtimi dilinin Visual C# için belgeleri kapsamıyordur çok puan dahil olmak üzere tüm yönleriyle ilgili ayrıntılı bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="5c45b-104">This specification contains detailed information about all aspects of the language, including many points that the documentation for Visual C# doesn't cover.</span></span>

<span data-ttu-id="5c45b-105">Sürümünden 5.0 bu belirtimi indirebilirsiniz [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=7029).</span><span class="sxs-lookup"><span data-stu-id="5c45b-105">You can download version 5.0 of this specification from the [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=7029).</span></span> <span data-ttu-id="5c45b-106">Visual Studio 2015 yüklediyseniz, belirtimi bilgisayarınızda Program Files (x86)/Microsoft Visual Studio 14.0/VC#/Specifications/1033 klasöründe bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c45b-106">If you've installed Visual Studio 2015, you can also find the specification on your computer in the Program Files (x86)/Microsoft Visual Studio 14.0/VC#/Specifications/1033 folder.</span></span> <span data-ttu-id="5c45b-107">Visual Studio yüklüyse başka bir sürümü varsa veya İngilizce dışındaki bir dilde Visual Studio yüklüyse, yolun uygun şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5c45b-107">If you have another version of Visual Studio installed or if you installed Visual Studio in a language other than English, change the path as appropriate.</span></span>

<span data-ttu-id="5c45b-108">Sürüm 6.0 belirtimi standart olarak onaylanmadı.</span><span class="sxs-lookup"><span data-stu-id="5c45b-108">Version 6.0 of the specification has not been approved as a standard.</span></span> <span data-ttu-id="5c45b-109">Bu sitedeki [ *taslak* C# 6.0 belirtimi](../../../../_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5c45b-109">This site contains the [*draft* C# 6.0 specification](../../../../_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="5c45b-110">İçinde yer alan markdown dosyalarını yerleşik [dotnet/csharplang GitHub deposuna](https://github.com/dotnet/csharplang/blob/master/spec/README.md).</span><span class="sxs-lookup"><span data-stu-id="5c45b-110">It is built from the markdown files contained in [the dotnet/csharplang GitHub repository](https://github.com/dotnet/csharplang/blob/master/spec/README.md).</span></span>

<span data-ttu-id="5c45b-111">Taslak belirtim sorunları oluşturulmalıdır [dotnet/csharplang](https://github.com/dotnet/csharplang/issues) deposu.</span><span class="sxs-lookup"><span data-stu-id="5c45b-111">Issues on the draft specification should be created in the [dotnet/csharplang](https://github.com/dotnet/csharplang/issues) repository.</span></span> <span data-ttu-id="5c45b-112">Veya, bulduğunuz hataları düzelttikten ilgileniyorsanız, size gönderebilirsiniz bir [çekme isteği](https://github.com/dotnet/csharplang/pulls) aynı deponuza.</span><span class="sxs-lookup"><span data-stu-id="5c45b-112">Or, if you are interested in fixing any errors you find, you may submit a [Pull Request](https://github.com/dotnet/csharplang/pulls) to the same repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c45b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c45b-113">See Also</span></span>  
 [<span data-ttu-id="5c45b-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5c45b-114">C# Reference</span></span>](../../language-reference/index.md)  
 [<span data-ttu-id="5c45b-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5c45b-115">C# Programming Guide</span></span>](../../programming-guide/index.md)

>[!div class="step-by-step"]
[<span data-ttu-id="5c45b-116">Next</span><span class="sxs-lookup"><span data-stu-id="5c45b-116">Next</span></span>](../../../../_csharplang/spec/introduction.md)

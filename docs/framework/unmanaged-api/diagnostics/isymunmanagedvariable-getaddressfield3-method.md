---
title: "ISymUnmanagedVariable::GetAddressField3 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1dfeb3f02b0c767dfc200a625fa4c617692dc11f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="a3a3c-102">ISymUnmanagedVariable::GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="a3a3c-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="a3a3c-103">获取此变量的第三个地址字段。</span><span class="sxs-lookup"><span data-stu-id="a3a3c-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="a3a3c-104">其含义取决于类型的地址。</span><span class="sxs-lookup"><span data-stu-id="a3a3c-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a3c-105">语法</span><span class="sxs-lookup"><span data-stu-id="a3a3c-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3a3c-106">参数</span><span class="sxs-lookup"><span data-stu-id="a3a3c-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a3a3c-107">[out]指向的指针`ULONG32`接收第三个地址字段。</span><span class="sxs-lookup"><span data-stu-id="a3a3c-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3a3c-108">返回值</span><span class="sxs-lookup"><span data-stu-id="a3a3c-108">Return Value</span></span>  
 <span data-ttu-id="a3a3c-109">如果该方法成功; 则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="a3a3c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3a3c-110">要求</span><span class="sxs-lookup"><span data-stu-id="a3a3c-110">Requirements</span></span>  
 <span data-ttu-id="a3a3c-111">**标头：** CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a3a3c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a3c-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3a3c-112">See Also</span></span>  
 [<span data-ttu-id="a3a3c-113">ISymUnmanagedVariable 接口</span><span class="sxs-lookup"><span data-stu-id="a3a3c-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="a3a3c-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="a3a3c-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="a3a3c-115">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="a3a3c-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="a3a3c-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="a3a3c-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)